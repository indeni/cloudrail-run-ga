# cloudrail-run-ga
GitHub action for including Indeni Cloudrail in a workflow.

# Instructions
This action requires several important inputs:
1. A Terraform plan that was generated using "terraform plan -out=plan"
2. A Cloudrail API key
3. An identifier of the cloud account you want to run Cloudrail against (if you have more than one added to Cloudrail).

The straight-forward way of using this action is:
```yaml
      - uses: indeni/cloudrail-run-ga@v1.0
        with:
          tf-plan-file: plan.out # This was created in a "terraform plan" step
          cloudrail-api-key: ${{ secrets.CLOUDRAIL_API_KEY }} # This requires registration to Indeni Cloudrail's SaaS
          cloud-account-id: 473085186055 # Replace this with your cloud account ID, which you've added to the Cloudrail SaaS
```

To see an example of how to use this action in a workflow, please take a look at https://github.com/indeni/cloudrail-demo/blob/master/.github/workflows/cloudrail-demo.yml
