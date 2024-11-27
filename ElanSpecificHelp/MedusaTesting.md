# Test locally via test
* Get production json
* Remove non-required components of the json
* Render data universe config in dev
* Update the test to use the series that has been rendered
* Veryify that data exists

# Deploy to awed

## Update json
* Update the json to include your changes
* Use medusa cli, something along the lines of the below (Ensure you test in dev)
```
python .\main.py --env dev add_series trimmed_means_5m_v2 --overwrite --config_path .\sample_input\prod_updated_2024-11-21.json
```

## Deploy medusa to dev
* Bump medusa-types version in medusa via PR
* Deploy this to dev using something like the following https://elancapital.visualstudio.com/medusa/_build?definitionId=300&_a=summary
* Build (medusa) processor. You will need to do this manually by going to resources and choosing your branch despite it claiming to have done it automatically for you
* processor dev deploy with your branch. you need to go to resources, processor/build processor and choose the latest run, as well as choosing your commit for clarity
* Create the new data universe https://awed-aks02-medusadev-medusa-server.dev01.elan-cap.com/docs#/Data%20Universe/rebuild_data_universe_data_universe__name__rebuild_post. A success response just mean it successfully kicked off the build, not that is built correctly. trimmed_means_5m_v2 is the largest universe
* can watch the universe deployement in rabbit is medusa-universe-create
or in argo medusadev-medusa-processor in awed which will have the live logs
* look in alert-medusa slack to see whether it was successful or not

## Deploy medusa to prod
* merge to master
* go to prod processor deployment 
* click approve
* repeat for prod deployment
* (update prod config)

# Api Urls
* Prod - https://awep-aks02-medusa-medusa-server.prod.elan-cap.com/docs#/Data%20Universe/rebuild_data_universe_data_universe__name__rebuild_post
* Dev - https://awed-aks02-medusadev-medusa-server.dev01.elan-cap.com/docs#/Data%20Universe/rebuild_data_universe_data_universe__name__rebuild_post