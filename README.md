# cloudrail-run-ga
GitHub action for including Indeni Cloudrail in a workflow.

# Instructions
This action requires several important inputs:
1. A Terraform plan that was generated using "terraform plan -out=plan"
2. A Cloudrail API key
3. An identifier of the cloud account you want to run Cloudrail against (if you have more than one added to Cloudrail).

The straight-forward way of using this action is:
```yaml
      - uses: indeni/cloudrail-run-ga@v1.1
        with:
          tf-plan-file: plan.out # This was created in a "terraform plan" step
          cloudrail-api-key: ${{ secrets.CLOUDRAIL_API_KEY }} # This requires registration to Indeni Cloudrail's SaaS
          cloud-account-id: 473085186055 # Replace this with your cloud account ID, which you've added to the Cloudrail SaaS
```

NOTE: If you're using Cloudrail in Static Analysis mode, without a cloud account, you can supply an empty `cloud-account-id` like so:
```yaml
      - uses: indeni/cloudrail-run-ga@v1.0
        with:
          tf-plan-file: plan.out # This was created in a "terraform plan" step
          cloudrail-api-key: ${{ secrets.CLOUDRAIL_API_KEY }} # This requires registration to Indeni Cloudrail's SaaS
          cloud-account-id: 
```

To see an example of how to use this action in a workflow, please take a look at https://github.com/indeni/cloudrail-demo/blob/master/.github/workflows/cloudrail-demo.yml

# Output

By default, this action will output in SARIF format, which is supported by GitHub, to list the security violations found by Cloudrail. To upload the SARIF into the GitHub system for analysis, use this:

```yaml
      - name: Upload SARIF file
        uses: github/codeql-action/upload-sarif@v1
        # Remember that if issues are found, Cloudrail return non-zero exit code, so the if: always()
        # is needed to ensure the SARIF file is uploaded
        if: always() 
        with:
          sarif_file: cloudrail_results.sarif
```

Note that it's not possible for the action to it automatically right now, due to the lack of [composite action support](https://github.com/actions/runner/issues/646).

By default, this action will output in SARIF format, which is supported by GitHub, to list the security violations found by Cloudrail.
