---
page_title: "Prisma Cloud: prismacloud_integration"
---

# prismacloud_integration

Manages an integration.

## Example Usage

```hcl
resource "prismacloud_integration" "example" {
    name = "SQS"
    integration_type = "amazon_sqs"
    description = "Made by Terraform"
    enabled = true
    integration_config {
        queue_url = "https://sqs.us-east-1.amazonaws.com/12345/url"
    }
}
```

## Argument Reference

* `name` - (Required) Name of the integration.
* `description` - Description.
* `integration_type` - (Required) Integration type (valid values can be found [here](https://api.docs.prismacloud.io/reference#integrations).
* `enabled` - (bool) Enabled.
* `integration_config` - (Required) Integration configuration, the values depend on the integration type, as defined [below](#integration-config).

### Integration Config

Refer to the [Prisma Cloud integration documentation](https://api.docs.prismacloud.io/reference#integration-configuration) if you need more information on a specific integration.

* `queue_url` - The Queue URL you used when you configured Prisma Cloud in Amazon SQS
* `login` - (Qualys/ServiceNow) Login.
* `base_url` - Qualys Security Operations Center server API URL (without "http(s)")
* `password` - (Qualys/ServiceNow) Password
* `tables` - (Map of bools) Key/value pairs that identify the ServiceNow module tables with which to integrate (e.g. - incident, sn_si_incident, or em_event).
* `version` - ServiceNow release version.
* `url` - Webhook URL.
* `headers` - List of webhook headers, as defined [below](#headers).
* `auth_token` - PagerDuty authentication token for the event collector.
* `integration_key` - PagerDuty integration key.
* `source_id` - GCP Source ID for Google CSCC integration.
* `org_id` - GCP Organization ID for Google CSCC integration.
* `api_key` - Demisto Api Key.
* `host_url` - ServiceNow URL/Jira/Demisto URL.
* `access_key` - Access Key for Demisto.
* `secret_key` - Secret Key for Jira/Demisto.
* `consumer_key` - Consumer Key for Jira integration.
* `jira_username` - Jira Username for Jira integration.
* `jira_password` - Jira App password Jira integration.
* `domain` - Okta Domain.
* `api_token` - Okta API token.
* `user_name` - Snowflake username.
* `pipe_name` - Snowflake pipename.
* `pass_phrase` - Snowflake PassPharse.
* `private_key` - Snowflake Private Key.
* `roll_up_interval` - File Roll up time for Snowflake.
* `staging_integration_id` - Amazon S3 integration Id for snowflake Integration.

### Headers

* `key` - (Required) Header name.
* `value` - (Required) Header value.
* `secure` - (bool) Secure.
* `read_only` - (bool) Read-only.

## Attribute Reference

* `integration_id` - Integration ID.
* `status` - Status.
* `valid` - (bool) Valid.
* `created_by` - Created by.
* `created_ts` - (int) Created timestamp.
* `last_modified_by` - Last modified by.
* `last_modified_ts` - (int) Last modified timestamp.
* `reason` - Model for the integration status details, as defined [below](#reason).
* `oauth_token` - Token for jira integration.

### Reason

* `last_updated` - (int) Last updated.
* `error_type` - Error type.
* `message` - Message.
* `details` - Model for message details, as defined [below](#details).

### Details

* `status_code` - (int) Status code.
* `subject` - Subject.
* `message` - Internationalization key.