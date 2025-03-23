# Assignment2.16# 
```
resource "aws_cloudwatch_metric_alarm" "lambda_error_alarm" {
  alarm_name                = "${local.name_prefix}-lambda-error-alarm"
  comparison_operator       = "GreaterThanThreshold"
  evaluation_periods        = 1
  metric_name               = "Errors"
  namespace                 = "AWS/Lambda"
  period                    = 300  # 5 minutes
  statistic                 = "Sum"
  threshold                 = 1  # Trigger alarm if more than 1 error occurs in 5 minutes
  alarm_description         = "This alarm triggers when the Lambda function has errors."
  dimensions = {
    FunctionName = aws_lambda_function.http_api_lambda.function_name
  }
  actions_enabled = true

  # Optional: Add SNS notifications or other actions
  # alarm_actions = ["arn:aws:sns:region:account-id:sns-topic"]
}
```
