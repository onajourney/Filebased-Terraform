# FS-Terraform

File system based terraform

# Installation

For playing around with aws infrastructure locally install LocalStack desktop and create a container.
Then deploy as you would.

`npm run init`

then plan or apply.

`npm run plan` or `npm run apply`

or use terraform directly within the infrastructure folder.

# TODO
- IMPLEMENT TTL into dynamodb tables
- IMPLEMENT write 

# POSSIBLE IMPROVEMENTS
- SHARE A AN EXECUTION ROLE AND ONLY DIVERGE FROM SHARING WHEN NEEDED (policies need to be attached)

# Notes


## Behaviours in LocalStack
- Changing view type by itself generates error ` ValidationException: Table already has an enabled stream` (Verified)
- Disabling and re-enabling a stream on a table generates error `ValidationException: Table already has an enabled stream` (Verified)
- Disabling stream still triggers lambda (Not in FS as false removes the `aws_lambda_permission` and the `aws_lambda_event_source_mapping` resource)
- Disabling stream only (not `stream_view_type`) will generate error `Table has no stream to disable`
- Even if stream is false and stream_view_type is not set stream seems to trigger as long as permission and mapping is present (not the case when table is first created)


HAHA