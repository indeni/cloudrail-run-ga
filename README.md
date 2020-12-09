# cloudrail-run-ga
GitHub action for including Clourdrail in a workflow.

# How to use this action?
This action requires several important inputs:
1. A Terraform plan that was generated using "terraform plan -out=plan"
2. A Cloudrail API key
3. An identifier of the cloud account you want to run Cloudrail against (if you have more than one added to Cloudrail).

To see an example of how to use this action, please take a look at https://github.com/indeni/cloudrail-demo/blob/master/.github/workflows/cloudrail-demo.yml
