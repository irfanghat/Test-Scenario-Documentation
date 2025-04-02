The following article outlines the sample documentation structure for each test scenario, which you can adapt and host accordingly.

### Sample Documentation Structure

Each scenario, should include:

-   **Overview**: A high-level description of the scenario.
-   **Preconditions**: Conditions that need to be met before running the scenario.
-   **Steps**: A list of steps to follow when running the scenario.
-   **Expected Result**: The expected outcome when the scenario executes successfully.
-   **Error Handling**: Possible errors that may occur and how they should be handled.
-   **Logs**: Example of the error traceback from the logs, as you provided.
    
----------

### Scenario 1: **Title**

**Overview**: Overview on the scenario.

**Preconditions**:
-   Condition 1.
-   Condition 2.
    
**Steps**:
1.  Step 1.
2.  Step 1.
3.  Step n.
    
**Expected Result**:

-   Something happens.
-   Another thing happens.
-   Another thing happens.
    
**Error Handling**:

-   **Error**: `workflowclienterror` with `unknown metadata error` occurs when doing somethingn.
-   **Solution**: Ensure everything is properly configured.
    
**Example Logs**:

```plaintext
Traceback (most recent call last):
  File "usr/local/lib/python3.8/site-packages/behave/model.py", line 1329, in run
    match.run(runner.context)
  File "usr/local/lib/python3.8/site-packages/behave/matchers.py", line 98, in run
    self.func(context, args, kwargs)
  File "tests/steps/manage_dataset.py", line 52, in step_impl
    dataset = update_dataset_context_update_payload(context.dataset_id, context.auth_token)
  File "src/manage_dataset.py", line 192, in update_dataset
    wait_for_async_request(request_id, auth_token)
  File "src/manage_dataset.py", line 355, in wait_for_async_request
    raise exception_str(response.json(), exception_errors)
Exception: workflowclienterror: unknown metadata error
Captured logs: src/manage_dataset created dataset 88939

```

----------

### Scenario 2: **Example scenario 2**
