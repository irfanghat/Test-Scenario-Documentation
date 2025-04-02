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

### Scenario 1: **Create Collection and Dataset Add It to the Collection and Check Dataset's Access Level**

**Overview**: This scenario tests the creation of a new collection and dataset, adding the dataset to the collection, and checking the access level of the dataset.

**Preconditions**:
-   User is authenticated and authorized to manage datasets and collections.
-   API tokens or authentication keys are available.
    
**Steps**:
1.  Create a new collection in the application.
2.  Create a dataset.
3.  Add the dataset to the newly created collection.
4.  Check the dataset's access level within the collection.
5.  Verify that the dataset is accessible as expected with the correct permissions.
    
**Expected Result**:

-   The collection and dataset are created successfully.    
-   The dataset is successfully added to the collection.
-   The dataset’s access level reflects the expected permissions.
    
**Error Handling**:

-   **Error**: `workflowclienterror` with `unknown metadata error` occurs when adding the dataset to the collection.
    
-   **Solution**: Ensure that the metadata is properly configured before performing the dataset addition operation. Retry the operation or consult the metadata documentation if issues persist.
    
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

### Scenario 2: **Fails Designation When Not In Collection**
**Overview**: This scenario tests the behavior when a dataset fails to be assigned a designation because it is not part of any collection.

**Preconditions**:
-   User has the necessary roles to assign designations to datasets.
-   The dataset is not already part of any collection.

**Steps**:

1.  Attempt to assign a designation to a dataset that is not part of any collection.
2.  Observe the system’s response to the invalid designation assignment.
    
**Expected Result**:
-   The system should return an error indicating that the dataset is not part of any collection and cannot be assigned a designation.

**Error Handling**:

-   **Error**: `dataset not in collection`
-   **Solution**: Ensure that the dataset is part of a collection before attempting to assign a designation.

**Example Logs**:

```plaintext
Traceback (most recent call last):
  File "usr/local/lib/python3.8/site-packages/behave/model.py", line 1329, in run
    match.run(runner.context)
  File "usr/local/lib/python3.8/site-packages/behave/matchers.py", line 98, in run
    self.func(context, args, kwargs)
  File "tests/steps/manage_designation.py", line 103, in step_impl
    result = assign_designation(context.dataset_id, context.auth_token)
  File "src/manage_designation.py", line 211, in assign_designation
    raise DatasetNotInCollectionError("Dataset not part of any collection")
Exception: DatasetNotInCollectionError: Dataset not part of any collection
Captured logs: src/manage_designation failed to assign designation to dataset 88432

```
