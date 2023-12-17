Getting started with AWS WAF
PDF
RSS
This tutorial shows how to use AWS WAF to perform the following tasks:

Set up AWS WAF.

Create a web access control list (web ACL) using the wizard in the AWS WAF console.

Choose the AWS resources that you want AWS WAF to inspect web requests for. This tutorial covers the steps for Amazon CloudFront. The process is essentially the same for an Amazon API Gateway REST API, an Application Load Balancer, an AWS AppSync GraphQL API, an Amazon Cognito user pool, an AWS App Runner service, or an AWS Verified Access instance.

Add the rules and rule groups that you want to use to filter web requests. For example, you can specify the IP addresses that the requests originate from and specify values in the request that are used only by attackers. For each rule, you specify how to handle matching web requests. You can do things like block or count them and you can run bot challenges like CAPTCHA. You define an action for each rule that you define inside a web ACL and for each rule that you define inside a rule group.

Specify a default action for the web ACL, either Block or Allow. This is the action that AWS WAF takes on a request when the rules in the web ACL don't explicitly allow or block it.

Note
AWS typically bills you less than US $0.25 per day for the resources that you create during this tutorial. When you're finished with the tutorial, we recommend that you delete the resources to prevent incurring unnecessary charges.

Topics
Step 1: Set up AWS WAF
Step 2: Create a Web ACL
Step 3: Add a string match rule
Step 4: Add an AWS Managed Rules rule group
Step 5: Finish your web ACL configuration
Step 6: Clean up your resources
Step 1: Set up AWS WAF

If you haven't already followed the general setup steps in Setting up, do that now.

Step 2: Create a Web ACL

The AWS WAF console guides you through the process of configuring AWS WAF to block or allow web requests based on criteria that you specify, such as the IP addresses that the requests originate from or values in the requests. In this step, you create a web ACL. For more information about AWS WAF web ACLs, see Web access control lists (web ACLs).

To create a web ACL
Sign in to the AWS Management Console and open the AWS WAF console at https://console.aws.amazon.com/wafv2/.

From the AWS WAF home page, choose Create web ACL.

For Name, enter the name that you want to use to identify this web ACL.

Note
You can't change the name after you create the web ACL.

(Optional) For Description - optional, enter a longer description for the web ACL if you want to.

For CloudWatch metric name, change the default name if applicable. Follow the guidance on the console for valid characters. The name can't contain special characters, white space, or metric names reserved for AWS WAF, including "All" and "Default_Action."

Note
You can't change the CloudWatch metric name after you create the web ACL.

For Resource type, choose CloudFront distributions. The Region automatically populates to Global (CloudFront) for CloudFront distributions.

(Optional) For Associated AWS resources - optional, choose Add AWS resources. In the dialog box, choose the resources that you want to associate, and then choose Add. AWS WAF returns you to the Describe web ACL and associated AWS resources page.

Choose Next.

Step 3: Add a string match rule

In this step, you create a rule with a string match statement and indicate what to do with matching requests. A string match rule statement identifies strings that you want AWS WAF to search for in a request. Usually, a string consists of printable ASCII characters, but you can specify any character from hexadecimal 0x00 to 0xFF (decimal 0 to 255). In addition to specifying the string to search for, you specify the web request component that you want to search, such as a header, a query string, or the request body.

This statement type operates on a web request component, and requires the following request component settings:

Request component – The part of the web request to inspect, for example, a query string or the body.

Warning
If you inspect the request components Body, JSON body, Headers, or Cookies, read about the limitations on how much content AWS WAF can inspect at Handling oversize web request components in AWS WAF.

For information about web request components, see Web request components.

Optional text transformations – Transformations that you want AWS WAF to perform on the request component before inspecting it. For example, you could transform to lowercase or normalize white space. If you specify more than one transformation, AWS WAF processes them in the order listed. For information, see Text transformations.

For additional information about AWS WAF rules, see AWS WAF rules.

To create a string match rule statement
On the Add rules and rule groups page, choose Add rules, Add my own rules and rule groups, Rule builder, then Rule visual editor.

Note
The console provides the Rule visual editor and also a Rule JSON editor. The JSON editor makes it easy for you to copy configurations between web ACLs and is required for more complex rule sets, like those with multiple levels of nesting.

This procedure uses the Rule visual editor.

For Name, enter the name that you want to use to identify this rule.

For Type choose Regular rule.

For If a request choose matches the statement.

The other options are for the logical rule statement types. You can use them to combine or negate the results of other rule statements.

On Statement, for Inspect, open the dropdown and choose the web request component that you want AWS WAF to inspect. For this example, choose Header.

When you choose Header, you also specify which header you want AWS WAF to inspect. Enter User-Agent. This value isn't case sensitive.

For Match type, choose where the specified string must appear in the User-Agent header.

For this example, choose Exactly matches string. This indicates that AWS WAF inspects the user-agent header in each web request for a string that is identical to the string that you specify.

For String to match, specify a string that you want AWS WAF to search for. The maximum length of String to match is 200 characters. If you want to specify a base64-encoded value, you can specify up to 200 characters before encoding.

For this example, enter MyAgent. AWS WAF will inspect the User-Agent header in web requests for the value MyAgent.

Leave Text transformation set to None.

For Action, select the action that you want the rule to take when it matches a web request. For this example, choose Count and leave the other choices as they are. The count action creates metrics for web requests that match the rule, but doesn't affect whether the request is allowed or blocked. For more information about action choices, see Rule action and Web ACL rule and rule group evaluation.

Choose Add rule.

Step 4: Add an AWS Managed Rules rule group

AWS Managed Rules offers a set of managed rule groups for your use, most of which are free of charge to AWS WAF customers. For more information about rule groups, see Rule groups. We'll add an AWS Managed Rules rule group to this web ACL.

To add an AWS Managed Rules rule group
On the Add rules and rule groups page, choose Add rules, and then choose Add managed rule groups.

On the Add managed rule groups page, expand the listing for the AWS managed rule groups. (You'll also see listings offered for AWS Marketplace sellers. You can subscribe to their offerings and then use them in the same way as for AWS Managed Rules rule groups.)

For the rule group that you want to add, do the following:

In the Action column, turn on the Add to web ACL toggle.

Select Edit and, in the rule group's Rules listing, open the Override all rule actions dropdown and select Count. This sets the action for all rules in the rule group to count only. This allows you to see how all of the rules in the rule group behave with your web requests before you put any of them to use.

Choose Save rule.

In the Add managed rule groups page, choose Add rules. This returns you to the Add rules and rule groups page.

Step 5: Finish your web ACL configuration

When you're done adding rules and rule groups to your web ACL configuration, finish up by managing the priority of the rules in the web ACL and configuring settings like metrics, tagging, and logging.

To finish your web ACL configuration
On the Add rules and rule groups page, choose Next.

On the Set rule priority page, you can see the processing order for the rules and rule groups in the web ACL. AWS WAF processes them starting from the top of the list. You can change the processing order by moving the rules up or down. To do this, select one in the list and choose Move up or Move down. For more information about rule priority, see Processing order of rules and rule groups in a web ACL.

Choose Next.

On the Configure metrics page, for Amazon CloudWatch metrics, you can see the planned metrics for your rules and rule groups and you can see the web request sampling options. For information about viewing sampled requests, see Viewing a sample of web requests. For information about Amazon CloudWatch metrics, see Monitoring with Amazon CloudWatch.

You can access summaries of the web traffic metrics on the web ACL's page in the AWS WAF console, under the Traffic overview tab. The console dashboards provide near real-time summaries of the web ACL's Amazon CloudWatch metrics. For more information, see Web ACL traffic overview dashboards.

Choose Next.

On the Review and create web ACL page, review your settings, then choose Create web ACL.

The wizard returns you to the Web ACL page, where your new web ACL is listed.

Step 6: Clean up your resources

You've now successfully completed the tutorial. To prevent your account from accruing additional AWS WAF charges, clean up the AWS WAF objects that you created. Alternatively, you can change the configuration to match the web requests that you really want to manage using AWS WAF.

Note
AWS typically bills you less than US $0.25 per day for the resources that you create during this tutorial. When you're finished, we recommend that you delete the resources to prevent incurring unnecessary charges.

To delete the objects that AWS WAF charges for
In the Web ACL page, select your web ACL from the list and choose Edit.

On the Associated AWS resources tab, for each associated resource, select the radio button next to the resource name and then choose Disassociate. This disassociates the web ACL from your AWS resources.

In each of the following screens, choose Next until you return to the Web ACL page.

In the Web ACL page, select your web ACL from the list and choose Delete.

Rules and rule statements don't exist outside of rule group and web ACL definitions. If you delete a web ACL, this deletes all individual rules that you've defined in the web ACL. When you remove a rule group from a web ACL, you just remove the reference to it.
