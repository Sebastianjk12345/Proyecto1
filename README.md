# bbog-dig-aws-frontend-iac
Terraform module for AWS Frontend (S3 + CloudFront + WAF + Route53 + Certificate Manager).

## Documentation
To see all the module documentation, do click [here](https://aws-frontend.github.labdigitalbdblifecycle.co/).

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| comment | The comment will be showed in your CloudFront distribution | string | `""` | yes |
| aliases | List of aliases might be associated to your CloudFront distribution | list(string) | `[]` | no |
| app_domain | Your application full domain | string | `""` | yes |
| app_name | The name of your web application | string | `""` | yes |
| tags | A mapping of tags to assign to the resources | map(string) | `{}` | no |
| cloudfront_distribution_tags | A mapping of tags to assign to the CloudFront distribution | map(string) | `{}` | no |
| certificate_tags | A mapping of tags to assign to the certificate | map(string) | `{}` | no |
| route53_domain | The domain of your existing Route53 zone or the domain you will create | string | `""` | yes |
| route53_tags | A mapping of tags to assign to the Route53 zone | map(string) | `{}` | no |
| waf_web_acl_id | Whether you want to pass an existing WAF for your CloudFront distribution | string | `""` | no |
| custom_error_responses | Custom error responses for your Cloudfront distribution | any | `[]` | no |
| certificate_arn | Optional ACM (banco) | string | `""` | no |
| create | Whether to create the Frontend UI App | bool | `true` | no |
| viewer_protocol_policy | Use this element to specify the protocol that users can use to access the files in the origin specified by TargetOriginId  | string | `"redirect-to-https"` | yes |
| target_origin_id | The value of ID for the origin that you want CloudFront to route requests to when a request matches the path pattern either for a cache behavior | string | `""` | yes |
| lambda_function_association | associate an AWS Lambda Function with a predefined event | any | `[]` | no |
| origins | all configure for origins | any | `[]` | no |
| domain_name | name of domain for origin | string | `""` | no |
| geo_restriction_locations | list for countries you want to pass traffic | list(string) | `["CO"]` | no |
| geo_restriction_restriction_type | The method that you want to use to restrict distribution | string | `"whitelist"` | no |
| create_validation | Whether to create a certifiacte validation | bool | `false` | no |
| forward_values_headers | Specifies the Headers, if any, that you want CloudFront to vary upon for this cache behavior | list(string) | `null ` | no |
| ordered_cache_behaviors | "all configure for behaviors" | any | `[]`  | no |
| enabled | Whether the distribution is enabled to accept end user requests for content | bool | `true` | no |

## Outputs

| Name | Description |
|------|-------------|
| this_cloudfront_distribution_id | The identifier for the distribution |
| this_cloudfront_distribution_arn | The ARN (Amazon Resource Name) for the distribution |
| this_cloudfront_distribution_caller_reference | Internal value used by CloudFront to allow future updates to the distribution configuration |
| this_cloudfront_distribution_status | The current status of the distribution. Deployed if the distribution's information is fully propagated throughout the Amazon CloudFront system |
| this_cloudfront_distribution_active_trusted_signers | The key pair IDs that CloudFront is aware of for each trusted signer, if the distribution is set up to serve private content with signed URLsThe key pair IDs that CloudFront is aware of for each trusted signer, if the distribution is set up to serve private content with signed URLs |
| this_cloudfront_distribution_domain_name | The domain name corresponding to the distribution |
| this_cloudfront_distribution_last_modified_time | The date and time the distribution was last modified |
| this_cloudfront_distribution_in_progress_validation_batches | The number of invalidation batches currently in progress |
| this_cloudfront_distribution_etag | The current version of the distribution's information |
| this_cloudfront_distribution_hosted_zone_id | The CloudFront Route 53 zone ID that can be used to route an Alias Resource Record Set to |
| this_cloudfront_origin_access_identity_id | The identifier for the distribution |
| this_cloudfront_origin_access_identity_caller_reference | Internal value used by CloudFront to allow future updates to the origin access identity |
| this_cloudfront_origin_access_identity_cloudfront_access_identity_path | A shortcut to the full path for the origin access identity to use in CloudFront |
| this_cloudfront_origin_access_identity_etag | The current version of the origin access identity's information |
| this_cloudfront_origin_access_identity_iam_arn | A pre-generated ARN for use in S3 bucket policies. Example: `arn:aws:iam::cloudfront:user/CloudFront Origin Access Identity E2QWRUHAPOMQZL` |
| this_cloudfront_origin_access_identity_s3_canonical_user_id | The Amazon S3 canonical user ID for the origin access identity, which you use when giving the origin access identity read permission to an object in Amazon S3 |
| this_waf_web_acl_id | The created or passed WAF web ACL ID |

