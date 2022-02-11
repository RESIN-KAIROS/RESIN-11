# RESIN-11
RESIN-11: Schema-guided Event Prediction for 11 Newsworthy Scenarios

## Schema Library
The schema library is in `schemas/scenario-schemas`. 
For each schema, we also provide visualizations and explanations in `schemas/hrf`.

## Instructions to Run the System
1. Run `git clone https://github.com/RESIN-KAIROS/RESIN-pipeline2022`

2. Run `cd RESIN-pipeline2022`

3. Setup `${KAIROS_LIB}` dir:
   - https://github.com/RESIN-KAIROS/RESIN-pipeline2022/blob/api/docker-compose.yaml#L8;

   - Uncompress data package (e.g, LDC2021E19_KAIROS_Quizlet_9_Source_Data_V1.0) and put everything under `${KAIROS_LIB}/resin/resin/input/task1`;

     e.g., `${KAIROS_LIB}/resin/resin/input/task1/{data,docs,tools}`

   - Put schemas library under `${KAIROS_LIB}/resin/resin/schemas`

4. Set up device number for each GPU-based component, e.g.,

   https://github.com/RESIN-KAIROS/RESIN-pipeline2022/blob/api/docker-compose.yaml#L57

5. Start APIs using: `docker-compose up`

6. Send the following POST message to the main API to start processing:

       curl -X POST --header "Content-Type: application/json" -d '{"id": "3fa85f64-5717-4562-b3fc-2c963f66afa6", "runId": "my_run_id", "sender": "string", "time": "2020-11-25T03:34:48.008Z", "content": {"data": "Example source document content here."}, "contentUri": "s3://kairos-experiment-data/performera/"}' http://0.0.0.0:10100/kairos/entrypoint

   - Output will be in this dir: `${KAIROS_LIB}/resin/resin/persist/${my_run_id}`

7. Send the following GET message to check the status:

       curl -X GET  http://0.0.0.0:10100/kairos/status

## Source code
Please view source code of each docker component in the docker-compose file.
