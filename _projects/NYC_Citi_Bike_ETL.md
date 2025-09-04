---
layout: post
title: Citi Bike NYC - A Data Engineering Approach
description: build end-to-end workflow from extract raw Citi Bike trip to process and analyze data
topic: data_engineering
---

Key objectives of the project include:

1. **Ingest historical weather data** from Open-Meteo API  
2. **Ingest Citi Bike data** from [NYC Trip Data](https://s3.amazonaws.com/tripdata/index.html)  
   - Supports both full load and monthly incremental load  
3. Upload data to **S3 raw zone**
4. Run **PySpark data transformations** via AWS Glue:
   - Convert datetime columns to timestamp
   - Filter out trips < 5 minutes
   - Remove trips starting and ending at the same station
5. Save cleaned data to **S3 clean zone** as Parquet
6. Populate AWS Glue Data Catalog using crawlers
7. Run **dbt** to build the `citibike_facts` table by joining trip data with weather

## Analysis & Visualization
- Use **Athena** or **Redshift Spectrum** to query
- Visualize insights via **Tableau**

<div class='tableauPlaceholder' id='viz1756232530250' style='position: relative'>
  <noscript>
    <a href='#'>
      <img alt='Dashboard '
           src='https://public.tableau.com/static/images/ci/citibiketwb_2025/Dashboard/1_rss.png'
           style='border: none' />
    </a>
  </noscript>
  <object class='tableauViz' style='display:none;'>
    <param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' />
    <param name='embed_code_version' value='3' />
    <param name='site_root' value='' />
    <param name='name' value='citibiketwb_2025/Dashboard' />
    <param name='tabs' value='no' />
    <param name='toolbar' value='yes' />
    <param name='static_image'
           value='https://public.tableau.com/static/images/ci/citibiketwb_2025/Dashboard/1.png' />
    <param name='animate_transition' value='yes' />
    <param name='display_static_image' value='yes' />
    <param name='display_spinner' value='yes' />
    <param name='display_overlay' value='yes' />
    <param name='display_count' value='yes' />
    <param name='language' value='en-US' />
  </object>
</div>

<script type='text/javascript'>
  var divElement = document.getElementById('viz1756232530250');
  var vizElement = divElement.getElementsByTagName('object')[0];
  if (divElement.offsetWidth > 800) {
    vizElement.style.width = '1000px';
    vizElement.style.height = '827px';
  } else if (divElement.offsetWidth > 500) {
    vizElement.style.width = '1000px';
    vizElement.style.height = '827px';
  } else {
    vizElement.style.width = '100%';
    vizElement.style.height = '2027px';
  }
  var scriptElement = document.createElement('script');
  scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';
  vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>

## Installation & Deployment
1. git clone https://github.com/sophie3101/data_projects.git

2. cd data_projects/03_nyc_citi_bike

3. Provision infrastructure:
  - cd terraform
  - terraform init
  - terraform apply  -var-file="secret.tfvars" 

4. Start airflow scheduler:
  - cd .. # back to the current directory of the project
  - astro dev init
  - astro dev start
  - Then start the pipeline dag

5. to generate `citibike_facts`, use dbt:
  - cd dbt_athena
  - dbt_init
  - dbt run

📍 More details of the project can be found: [github_link](https://github.com/sophie3101/data_projects/tree/main/03_nyc_citi_bike)


