# dbt_deployment

This project aims to develop SQL models in dbt and schedule these models in platforms like Apache Airflow (Google Cloud Composer), Dbt Cloud, Google Cloud Run. The project aimed to explore and leverage the full range of data operations available for DBT workflows.

# Solution Architecture


Users write dbt code in their text editor of choice and then invoke dbt from the command line. 
Upload the Dbt project and Airflow DAG from the Local system to the dags folder in the gcs bucket created by the composer environment.
The Airflow DAG will run on a scheduled basis and write results to snowflake.
Push the dbt project to GitHub repo and integrate with dbt cloud and schedule jobs in dbt which will write results to BigQuery.
Every time code is pushed to github master branch, cloud build will trigger and create a new docker image push to container registry and then a cloud run service will be deployed with the latest image. 
Cloud scheduler will trigger the cloud run url at the scheduled time and write the results to bigquery.
