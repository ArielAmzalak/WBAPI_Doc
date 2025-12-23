+++
id = "template-categorization"
title = "Template categorization"
summary = "When creating a new template, or managing existing ones, it's important to understand how WhatsApp categorizes your template for pricing purposes."
source = "https://developers.facebook.com/docs/whatsapp/template-categorization"
lang = "en"
tags = ["whatsapp-business-platform", "marketing-messages-lite-api", "messaging", "templates", "phone-numbers", "authentication"]
+++
# Template categorization

When creating a new template, or managing existing ones, it's important to understand how WhatsApp categorizes your template for pricing purposes.

1. Consider template category guidelines before creating a new template
2. Stay updated on your template's approval status after template creation
3. Learn about automatic category updates to templates in production

***This information is also available in PDF form in our [Message templates category guidelines explainer PDF](https://scontent.fcgb9-1.fna.fbcdn.net/v/t39.8562-6/522646671_1032957015586071_352200442705405080_n.pdf?_nc_cat=108&ccb=1-7&_nc_sid=b8d81d&_nc_ohc=a6BcFr1u46wQ7kNvwHc8QoI&_nc_oc=AdloKyd4h6jMqvuG0XyYrXqsiXeomRxaJfimvUN_QuHmfCdqHXhLjNV6zO9t3vTPAjA&_nc_zt=14&_nc_ht=scontent.fcgb9-1.fna&_nc_gid=YIjQ2Zf8QYCh886aA3HYxg&oh=00_AfgqTDKMz9NPge06_6hyzavfl5YSbRJScUPM52FhWQwyCA&oe=692BDD22).***

## Template category guidelines

Our template category guidelines define the category of message templates. Message templates can be categorized as:

* **Marketing templates**  Enable businesses to achieve a wide range of goals, from generating awareness to driving sales and retargeting customers.
* **Utility templates**  Enable businesses to follow up on user actions or requests, since these messages are typically triggered by user actions.
* **Authentication templates**  Enable businesses to verify a users identity, potentially at various steps of the customer journey.

### Marketing template guidelines

Marketing templates are the most flexible. They enable businesses to achieve a wide range of goals, from generating awareness to driving sales and more.

*Note: Examples are illustrative only. Templates that contain similar content, or the example text above, might be categorized differently based on the exact content.*

#### Message Objective: **Awareness**

| Business Goal | Example Templates |
| --- | --- |
| Generate awareness of your business, products, or services among customers who have subscribed to receive messages from your business on WhatsApp. | * Did you know? We installed a {{new\_tower}} in your area so you can enjoy a better network experience. To learn more, visit our site. * {{Diwali}} is around the corner! Join us at {{location}} on {{date}} to celebrate with friends and family. For more details about our event, click below. * Looking for a getaway this fall? Our newest resort just opened in {{location}}: the perfect place to relax and unwind. |

#### Message Objective: Sales

| Business Goal | Example Templates |
| --- | --- |
| Send promotional offers to customers related to sales events, coupons, or other content intended to drive sales or renewals. | * As a thank you for your last order, please enjoy {{15}}% off your next order. Use code {{loyal15}} at checkout. Visit our site here below. * We are actively seeking {{donations}} to meet our fundraising goal of {{amount}}. Support our cause and contribute now!- Upgrade to our {{premium\_cabin}} to enjoy new benefits, like {{more\_legroom}} and {{priority\_boarding}}. Click below or log into our app to upgrade. * You have been {{pre\_approved}} for our {{credit\_card}}! Enjoy an introductory {{apr\_rate}} if you apply via your personalized link below. |

#### Message Objective: **Retargeting**

| Business Goal | Example Templates |
| --- | --- |
| Promote or recommend offers, products or services; attempt to renew subscriptions; or other calls to action to users who might have visited your website, used your app or engaged with you. These are marketing even if requested by users. | * Your subscription will expire on {{date}}! Renew today to save {{discount}}. * You left {{items}} in your cart! Dont worry, we saved them. Checkout now below. * Your loan application is {{pending\_approval}}! Please log in to pick up where you left off. * We found a {{car}} that meets your saved search. Log in to our app to view. * We apologize for the delay in your {{package}} delivery. We have deposited a {{credit}} to your account, available immediately. |

#### Message Objective: **App Promotion**

| Business Goal | Example Templates |
| --- | --- |
| Request customers to install or take a specific action with your app. | * Did you know? You can now {{checkout}} in our app. Download it below to use our streamlined experience. * Thank you for using our app. We noticed you have not used our {{latest\_feature}}. Click below to learn more about how this benefits you! * In-app only: {{20}}% off this week! Use code {{summer\_promo}} to save on select styles. * Hi {{name}}, your friend {{name}} recently joined our community. Send them a welcome message in our app today: {{URL}}. |

#### Message Objective: **Build Customer Relationships**

| Business Goal | Example Templates |
| --- | --- |
| Strengthen customer relationships through personalized messages or by prompting new conversations. | * {{Name}}, did you think wed forget? No way! {{Happy\_birthday}}! We wish you the best in the year ahead. * As we approach the end of the year, we reflect on what drives us: {{Name}}. Thank you for being a {{valued\_customer}}. We look forward to continuing to serve you. * Hello, I am the new {{virtual\_assistant}}. I can help you discover products or provide support. Please reach out if I can help! |

The following templates are also considered marketing:

* Templates with mixed content (for example, both utility and marketing, such as an order update with a promo or a feedback survey with promotional content).
* Templates where contents are unclear (for example, where contents are only {{1}} or Congratulations!).

### Utility template guidelines

Utility templates are typically triggered by a user action or request. For a template to be categorized as utility, it needs to meet both criteria below:

* *Must* be **non-promotional**, not containing any promotional or persuasive intent.
* *Must* ALSO be either **specific to or requested by the user** (clearly related to their order, account, services or transactions) OR **essential or critical** to the user (for example, to ensure user safety).

#### Message Objective: **Opt-In Management on WhatsApp**

| Business Goal | Example Templates |
| --- | --- |
| Confirm opt-in to receive messages on WhatsApp as a follow-up to opt-in collected via other channels (for example, website, email) or confirm opt-out. | * Thanks for confirming opt-in! Youll now receive notifications via WhatsApp. * Thank you for confirming your opt-out preference. You will no longer receive messages from us on WhatsApp. |

#### Message Objective: **Order Management**

| Business Goal | Example Templates |
| --- | --- |
| Confirm, update or cancel an order or transaction with a customer, using specific order or transaction details in the body of your message.  *These messages should not promote, recommend, upsell, or cross-sell products; include offers; or attempt to secure renewals.* | * Thank you! Your order {{order\_number}} is confirmed. We will let you know once your package is on its way. * Hooray! Your package from order {{order\_number}} is on its way. Your tracking number is {{tracking\_ID}} and expected delivery date is {{date}}. * Unfortunately, one item from your order {{number}} is backordered. We will follow up with an estimated ship date. If you wish to cancel and receive a refund, please click below. * We have received your item from order {{order\_number}}. Your refund for ${{amount}} has been processed. Thank you for your business. |

#### Message Objective: **Account Alerts or Updates**

| Business Goal | Example Templates |
| --- | --- |
| Send important or time-sensitive updates or alerts or other information specific to purchased or subscribed products/services.  *These messages should not promote, recommend, upsell, or cross-sell products; include offers; or attempt to secure renewals.* | * Daily update for account ending in {{four\_digit\_number}}: Your available balance is {{amount}}. * Reminder: Your monthly payment for {{service}} will be billed on {{date}} to the {{card}} you have saved on file. * You only have {{number}} minutes remaining in your plan. Remember to top up your account by {{date}} to avoid disruptions. * To finish setting up your {{new\_profile}}, you need to upload a {{photo}}. Please click below to upload. * Please note, we have updated our {{Customer\_service}} phone number to {{number}}. Please save this and call if we can be of support. |

#### Message Objective: **Feedback Surveys**

| Business Goal | Example Templates |
| --- | --- |
| Collect feedback on previous orders, transactions or engagements with customers.  *Specificity of the order or interaction to which these relate is necessary. A general/generic survey or request for feedback will not be approved as utility.* | * We have delivered your order {{order\_number}}! Please let us know if there was any issue by reaching out below. * Your feedback ensures we continually {{improve}}. Please click below to share your thoughts on your {{recent visit}} at our {{store}} location. Thank you in advance! * You chatted with us {{online}} recently about order {{order\_number}}. How was your experience? Click below to fill out a short survey. |

#### Message Objective: **Continue a Conversation on WhatsApp**

| Business Goal | Example Templates |
| --- | --- |
| Send a message to begin an interaction on WhatsApp that began in another channel.  *These messages should not be initiated without a user having requested the conversation to be moved to WhatsApp.* | * Hi! I see you requested support via our {{online\_chat}}. I am the virtual assistant on WhatsApp. How can I help? * Hi {{name}}, we are following up on your call with customer service on {{issue}}. Your case has progressed to the next step. Please log into your account to continue. |

For a utility template to be deemed essential or critical to the user, it must reflect one of the use cases below and must also be non-promotional (not containing any promotional or persuasive intent).

**Public safety utility use case:**

| Use case | Example that meets definition of "essential or critical to the user" |
| --- | --- |
| Severe weather | There is a {{tornado}} alert in your area. We recommend you remain indoors until {{time}} today. |
| Crisis response | We activated support services for the {{crisis}} in the {{zip code}} area. Live updates on our site, available below. |

**Public service use case:**

| Use case | Example that meets definition of "essential or critical to the user" |
| --- | --- |
| Health awareness | Stay up-to-date with your health. Stop by {{location}} by {{time}} to get your free COVID-19 {{vaccine}}. Bring your {{vaccination\_card}} and identification document. |
| Health emergency | The {{city}} has just declared a health emergency because of {{issue}}. We will follow up with more details once available. |
| Voting registration | To vote on {{date}}, please ensure your voter {{registration card}} is active. Please click the URL below to understand steps required to renew, if needed. Please disregard this message if your {{registration card}} will be active. |
| Disbursements | Your {{welfare}} disbursement balance is {{amount}}. Kindly note it will expire on {{date}}. |

**Public disruption use case:**

| Use case | Example that meets definition of "essential or critical to the user" |
| --- | --- |
| System outages | We have detected a system outage that impacts zip code {{code}}. We expect to restore service by {{time\_and\_date}}. We apologize for the inconvenience. |
| Operational disruption | This is to notify you that {{trains}} at our {{location}} station are halted because of {{issue}}. Please avoid the area as we work to rectify. |

**Account or product protection use case:**

| Use case | Example that meets definition of "essential or critical to the user" |
| --- | --- |
| Fraud awareness | We have detected an increase in {{ATM fraud}}. To protect your card ending in {{1234}}, please consider updating your PIN. Click below to see the step-by-step. |
| Product recalls | The {{product}} you ordered on {{date}} has been recalled. Please click below to let us know how you would like to proceed. |
| Warranty alerts | Thank you for your purchase of {{product}}. Your warranty is active as of {{date}}. Our {{product manuals}} are below, for your reference |

**Legal/regulatory compliance use case:**

| Use case | Example that meets definition of "essential or critical to the user" |
| --- | --- |
| Identity compliance | This is to notify you that you need to upgrade to a {{updated\_identification\_card}} by {{date}}. To avoid any inconveniences when traveling, please ensure you make an appointment at your local {{office}}. |
| Privacy disclosures | We updated our privacy policy on {{date}}. Please click the button below to learn more. |
| Warranty alerts | Thank you for your purchase of {{product}}. Your warranty is active as of {{date}}. Our {{product manuals}} are below, for your reference |

### Authentication template guidelines

**Only authentication templates can be used to send a one-time passcode for identity verification. Marketing and utility templates cannot be used for this purpose.**

Businesses on Cloud API can use authentication templates from [Template Library](/docs/whatsapp/cloud-api/guides/send-message-templates/template-library).

Authentication templates enable businesses to verify user identity (usually with alphanumeric codes) at various steps of the customer journey:

* New account creation
* Account integrity, access or recovery
* New or existing orders/transactions

Authentication templates are our most restrictive, so for a template to be classified as authentication, **a business must**:

* Use Cloud API authentication message templates in [Template Library](/docs/whatsapp/cloud-api/guides/send-message-templates/template-library): These templates include optional add-ons like security disclaimers and expiry warnings.
* Configure a one-time password button: Such as [copy-code](/docs/whatsapp/business-management-api/authentication-templates/copy-code-button-authentication-templates) or [one-tap](/docs/whatsapp/business-management-api/authentication-templates/autofill-button-authentication-templates)
* Follow content restrictions: URLs, media, and emojis are not allowed for authentication template content or parameters. Parameters are also restricted to 15 characters.

#### Message Objective: **Authentication**

| Business Goal | Example Templates |
| --- | --- |
| Authenticate users with one-time passcodes | * "{{1}} is your verification code." * "{{1}} is your verification code. For your security, do not share this code." * "{{1}} is your verification code. This code expires in 15 minutes." |

## How we assign a category during template creation

When you create a template, you indicate the template's category, based on the guidelines above. We validate the category you indicated per the contents of the template and our [guidelines](#template-category-guidelines). We will then create the template and set its status to one of the statuses below, based on the outcome of the validation process.

a. When you create a template and we approve it, you can request a review up to 60 days from the creation date.

b. For utility templates we might update to marketing, you can request a review up to 60 days from the date we updated the category.

### Approved status

`APPROVED` status means we agree with the category chosen in your template creation request and that the template successfully passed [template review](/docs/whatsapp/business-management-api/message-templates#template-review). It can now be used to send messages.

**Status updates**  An email and WhatsApp Manager alert will inform you that the template was approved, and a [message\_template\_status\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_status_update) webhook will be triggered with the event property set to `APPROVED`.

Effective April 9, 2025, If you selected `UTILITY` as the templates category and we determine it should be `MARKETING`, **we approve the template as `MARKETING`**. In WhatsApp Manager, you will see the screen below. When using the API, the behavior will be as outlined above. You can request a review up to 60 days from the date we updated the category.

Effective April 9, 2025  We no longer support the `allow_category_change` property during template creation. Previously, if set to `true` in a template creation request, this allowed us to update a templates category to `marketing`, if we determined `marketing` to be its category per its content and our guidelines. This is now the default behavior.

### Pending status

`PENDING` status means we agree with the category chosen in your template creation request, however the template is undergoing [template review](/docs/whatsapp/business-management-api/message-templates#template-review).

**Status Alerts**  The outcome of template review will be communicated via email and WhatsApp Manager alert. Upon completion, a [message\_template\_status\_update](/docs/whatsapp/business-management-api/webhooks/components#message-template-updates) webhook will be triggered with the event property set to `APPROVED` or `REJECTED`.

### Rejected status

`REJECTED` status indicates that we disagreed with the category you designated in your template creation request.

**Status Alerts**  Rejections are communicated via email and WhatsApp Manager alert. Upon review completion, a [message\_template\_status\_update](/docs/whatsapp/cloud-api/webhooks/reference/message_template_status_update) webhook will be triggered and the `event` property set to `REJECTED`, with the `reason` property set to `INCORRECT_CATEGORY`.

If your message template is rejected, you have the following options:

* [Create a new message template](/docs/whatsapp/business-management-api/message-templates/) via WhatsApp Manager or the API.
* [Edit the template's category](/docs/whatsapp/business-management-api/message-templates/template-management#edit-templates), and resubmit for approval.
* [Request a review](#how-to-request-a-category-review).

### Duplicated Templates from Phone Number Migration

All eligible templates are automatically duplicated in the destination WABA and category checks will be performed to ensure that all duplicated templates are correctly categorized.

## How we update a template's category after initial approval

July 1, 2024  To ensure templates on our platform are correctly categorized per our template category guidelines, we introduced a recurring process to identify and update approved templates that should be of a different category, per our template category guidelines.

Effective April 16, 2025  For any business we detect to be abusing our template categorization system and to whom [we send a warning](#notices-when-action-is-taken), we will no longer provide the 24-hour notice mentioned below if we detect a utility template that should be marketing. We will update the category with no advance notice and trigger emails/webhooks to confirm the category change

Automatic category updates can apply to approved templates only that were not initially approved per our template category guidelines. We provide advance notice on different surfaces, like through webhook and email, before we take action on these templates.

Read on to learn specifics about how we handle this process.

### **How it works**

### For templates approved as **utility**, but should actually be **marketing**

* **Notice period**  We provide 1-day advance notice before **the template category is updated to `marketing`**.
* **As of April 16 2025  If you are warned for template categorization misuse:**
* 24 hour notice **will not** be provided before changing template categories from `UTILITY` to `MARKETING`
* Category changes will be **instant**
* **Template category**  The template category is changed to `MARKETING`
* **Template status**  There is no change to template status; it remains `APPROVED` and can continue to be used to send messages.

### For templates approved as **marketing or utility**, but should actually be **authentication**

*This process was introduced on October 1, 2024*

* **Notice period**  We provide advance notice.
* **Template category**  There is no change in the templates category.
* **Template status**  On the first day of the following month, the template status is changed to `REJECTED` and can no longer be used to send messages.

### **How we notify you**

### For templates approved as **utility**, but should actually be **marketing**

| Advanced notification of category updates | Description |
| --- | --- |
| *Via Email* | * An email will be sent to any people in the business portfolio with full control of the WhatsApp Business Account (WABA). * The email will contain a link to the WhatsApp Manager > Message Templates > Manage Templates panel. * Templates whose categories will be updated will have an "information" icon beside their name. Hovering over the icon will display the category it will be updated to, and the date when it will be updated. * For templates that will be rejected, the icon will display |
| *Via Webhook* | A [template\_category\_update](/docs/whatsapp/cloud-api/webhooks/reference/template_category_update) webhook webhook will be triggered for each template whose category will be updated, with a `correct_category` property in the payload set to what the template's category should be. The `new_category` property also exists in the payload indicating the templates current category. |
| *Via WhatsApp Manager* | * The WhatsApp Manager > Message Templates > Manage Templates panel will display a banner with a link to a downloadable CSV identifying these templates. * [Business Support](https://business.facebook.com/business-support-home/) will list the name and current category of these templates, as well as the categories they will be updated to. |

| Notification when action is taken | Description |
| --- | --- |
| *Via Email* | * An email will be sent to any people in the business portfolio who have been granted full control of the WABA that owns the templates whose categories have been updated. * The email will highlight the number of templates whose categories were updated, and will include a link to the WhatsApp Manager > Message Templates > Manage Templates panel where the name and new category of these templates, as well as the categories before automatic update will be listed. It also includes a link to [Business Support](https://business.facebook.com/business-support-home/). |
| *Via Webhook* | A [template\_category\_update](/docs/whatsapp/cloud-api/webhooks/reference/template_category_update) webhook webhook will be triggered for each template whose category has been updated. The `new_category` property will indicate the template's new category and the `previous_category` property will indicate the template's category before automatic update. |

### For templates approved as **marketing or utility**, but should actually be **authentication**

| Advanced notification of category updates | Description |
| --- | --- |
| *Via Email* | * An email will be sent to any people in the business portfolio who have been granted full control of the WABA that owns the templates whose categories have been updated. * The email will contain a link to the WhatsApp Manager > Message Templates > Manage Templates panel. * Templates whose status will be updated to `REJECTED` will be updated will have an "information" icon beside their name. Hovering over the icon will display the date when the template will be rejected. |
| *Via Webhook* | * A [template\_category\_update](/docs/whatsapp/cloud-api/webhooks/reference/template_category_update) webhook will be triggered for each template which will be rejected. |
| *Via WhatsApp Manager* | * The WhatsApp Manager > Message Templates > Manage Templates panel will display a banner with a link to a downloadable CSV identifying these templates. [Business Support](https://business.facebook.com/business-support-home/) will list these as well. |

| Notification when action is taken | Description |
| --- | --- |
| *Via Email* | * An email will be sent to any people in the business portfolio who have been granted full control of the WABA that owns the templates whose categories have been updated. * The email will highlight the number of templates that were rejected, and will include a link to the WhatsApp Manager > Message Templates > Manage Templates panel, where the status will reflect the template is rejected. * It also includes a link to [Business Support](https://business.facebook.com/business-support-home/). |
| *Via Webhook* | A `status` webhook will be triggered for each template that has been rejected. whose category has been updated. The webhook will have the `event` property set to `REJECTED` and the reason property set to `INCORRECT_CATEGORY`. |

### Your options in this process

When you receive notice that a templates category will be updated or a template will be rejected, you can:

* Create a new template
* For **utility templates** that will be updated to **marketing**:
  + You can [request a review](#how-to-request-a-category-review):
    - If the review is approved  The templates category will not be updated as previously notified.
* If the review is not approved  The template will be updated to marketing, as previously notified.
* For **marketing or utility templates** that will be **rejected**:
  + You cannot request a review.
  + Businesses on Cloud API can browse our [template library](/docs/whatsapp/cloud-api/guides/send-message-templates/template-library) to identify available options for your identity verification use case. We recommend businesses browse, choose and create a new template from the [template library](/docs/whatsapp/cloud-api/guides/send-message-templates/template-library) before the utility/marketing template is rejected, to avoid workflow disruptions.

**You have 60 days to review and appeal these changes in [Business Support Home](https://business.facebook.com/business-support-home/).**

### Learn which template(s) will be updated or have been updated

### Via API

You can use the [`GET /<WHATSAPP_BUSINESS_ID>/message_templates`](/docs/graph-api/reference/whats-app-business-account/message_templates/) endpoint to get the list of templates that have been or will be updated.

Request the `category` and `correct_category` fields, which will return the IDs of all of the WABA's templates, and each template's `category` and `correct_category` values. You can then compare these values:

```
GET /<WHATSAPP_BUSINESS_ID>/message_templates?fields=category,correct_category
```

* If the values match (for example, they are both `MARKETING`), the template's category has already been updated with the `correct_category` value.
* If they mismatch and the `correct_category` is not an empty string or null (for example, category is `UTILITY` but `correct_category` is `MARKETING`), the template's category will be updated on the first day of the next month with the `correct_category` value.
* If the `correct_category` value is an empty string or null, the template has not been impacted.

### Via WhatsApp Manager

The WhatsApp Manager's Manage Templates panel identifies any templates whose categories will be updated.

## How to update a template category or request a category review

This process has been in effect since June 2023, when we introduced our marketing, utility and authentication template categories.

### Edit your template's category

#### Via API

You can [edit template content or just its category](/docs/whatsapp/business-management-api/message-templates/template-management#edit-templates).

* The template will undergo category validation and template review again.
* If the template passes validation and review, its category will be updated and a [template\_category\_update](/docs/whatsapp/cloud-api/webhooks/reference/template_category_update) webhook webhook will be triggered.
* The `new_category` property in the webhook payload will indicate its new category.

#### Via WhatsApp Manager

On the **Manage Templates** tab:

1. Select your template
2. Edit the content so it aligns to the guidelines of that category
3. Re-submit the template for approval

If the template passes validation and review, its category will be updated and a [template\_category\_update](/docs/whatsapp/cloud-api/webhooks/reference/template_category_update) webhook webhook will be triggered. The `new_category` property in the webhook payload will indicate its new category.

### Qualifications and outcomes for category review:

You can request Meta to review the category of your template if:

* It is categorized as `UTILITY` or `MARKETING` and status is `REJECTED`
* It is categorized as `MARKETING` and status is `APPROVED`

Possible outcomes after you submit a request of your templates category:

* Review is approved  The category will be updated. A [template\_category\_update](/docs/whatsapp/cloud-api/webhooks/reference/template_category_update) webhook webhook will be triggered. The `new_category` property in the webhook payload will indicate its new category.
* Review is rejected  The category will not change.

### How to request a category review

A review can only be requested via WhatsApp Manager.

In the sidebar of WhatsApp Manager, select the **Message Templates** dropdown, and then **Message Templates**. You should see a rejection banner with the template in question. Click **Go to Business Support**.

Click **Template Category Updates**, select the templates you would like reviewed and then click the **Request Review** button to begin the review process.

### How to view templates submitted for review:

In the Business Support sidebar, click **Template category Updates**, and then the **In review** tab.

### How to view template category decisions

**If the template category change is not approved**: The template can be viewed in Business Support under the **Template category updates** > **Unchanged** tab. The templates category will change to the correct category during an automatic category update.

**If the template category change is approved**: the template can be viewed in Business Support under the **Template category updates** > **Reversed** tab. If the template category was already changed during automatic category update, it will be reverted to its previous category.

## Restrictions on businesses misusing the template categorization system

### How it works

We provide written notice before we restrict businesses from using the WhatsApp Business Platform for utility messaging in the following way:

* **Warning**  If we detect a business is misusing our template categorization system to secure the utility category for templates that should be categorized as marketing, we will send a written warning before we restrict them from using utility messaging on the WhatsApp Business Platform.
* **As of April 16 2025  After you are given a warning:**
* A 24 hour notice **will not be provided** before changing template categories from `UTILITY` to `MARKETING`
* Category changes will be **instant**
* **Restriction**  If we detect misuse after this warning, we will introduce the following restrictions which would prevent the WhatsApp Business Account from using the WhatsApp Business Platform for utility messaging for 7 days:
* **As of April 16 2025  We will no longer reject all previously approved `UTILITY` templates. Instead, they will be re-categorized as `MARKETING`**
* For 7 days  Disable [category reviews](#how-to-request-a-category-review) for these templates
* For 7 days  Disable creation of new utility templates

**For businesses that have been restricted previously**  If we detect continued misuse of our template categorization system, we might re-introduce these restrictions for 30 days.

### Notices when action is taken

We trigger the following notices:

* **Warnings**  Email is sent to all WhatsApp Business Account admins (people with **Full control** of the WhatsApp Business Account). An `account_update` webhook will be sent out indicating utility restriction `WARN` for the WhatsApp Business Account.
* **Restrictions**  When we introduce or lift restrictions, email is sent to all WhatsApp Business Account admins (people with **Full control** of the WhatsApp Business Account). We also trigger a change to the `restriction_info` object in the `account_update` webhook.

### Your options in this process

Businesses that believe we have applied these restrictions in error can request a review via [Business Support](https://business.facebook.com/business-support-home/).
