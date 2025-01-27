# CircleCI Usage API Exporter

## Introduction

This tool outlines using the CircleCI Usage API to create and download usage reports. The data is then merged and transformed into a graph to show credit usage per project.

For more info on the API itself, visit the docs [here](https://circleci.com/docs/api/v2/index.html#tag/Usage).

All the outputs are saved as an [artifact](https://circleci.com/docs/artifacts/) on CircleCI.

### Use Cases

While the implementation shown in this project is simple, there are many use cases for implementing the Usage API in this way. 

Some of the advantages include:

- [Scheduling the pipeline](https://circleci.com/docs/scheduled-pipelines/) to run weekly, to enable users to target projects that have a higher credit usage
- Enabling the comparison of weekly results
- Can be combined with the [Slack orb](https://circleci.com/developer/orbs/orb/circleci/slack) to send notifications on specific usage metrics
- Can be amended to target job-level data instead, to track the cost of failing jobs
- Can group projects by team, to enable cross-company billing

## Tools

To learn more about working with `*.csv` files, and transforming the data once it's downloaded, check out [pandas](https://pandas.pydata.org/).

To learn more about graphs using python, check out [Matplotlib](https://matplotlib.org/stable/).

## Requirements

- A CircleCI [personal API token](https://circleci.com/docs/managing-api-tokens/#creating-a-personal-api-token) is required in order to use the API. This is saved with the name `CIRCLECI_API_TOKEN`, in a context.
- A date range is required. These are specified using the `START_DATE` and `END_DATE` environment variables
- An organisation ID is required. This defaults to the ID of the organisation that is executing the job on CircleCI.

### Caveats

- My python skillz aren't great