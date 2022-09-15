## Uffizzi Quickstart Example App - Establish A Uffizzi Preview Environment in 3 steps
=========

## 1. Fork this Repo
## 2. Enable GHA workflows in your Repository
## 2. Open a PR of `try-uffizzi` branch against `main` in your fork

That's it!

The PR will trigger a series of [jobs](https://github.com/UffizziCloud/quickstart/blob/main/.github/workflows/uffizzi-environment.yml) with Uffizzi Github Action's re-useable [workflow](https://github.com/marketplace/actions/create-preview-environment) being utilized to create an on-demand preview environment for this example micro-services application.  The environment URL and Uffizzi Dashboard URL will be posted as a comment in your PR when the workflow completes.

-New commits will update the environment.  
-Merging or Closing the PR will delete the environment.  
-The environment is set to `delete` in 1hr 

The environment is defined by [docker-compose](https://github.com/UffizziCloud/quickstart/blob/main/docker-compose.template.yml).

From within the Uffizzi Dashboard you can view logs and events, manage projects, manage teams, set RBAC, set SSO, and establish password protected URLs.

**Note-** Running this workflow will create a free Uffizzi Platform account under the Github account from which it is initiated.  Each account receives 10,000 preview minutes per month for free.  If you exceed the free tier threshold your services will be paused until you provide a credit card.  Users are not liable for paid services unless they authorize billing.

Using Uffizzi for Crypto-mining, bots and other unauthorized activities is strictly prohibited per the user policy.  Users who break the service agreement are at risk of being banned from future use.  

Architecture of this Example App
-----

![Architecture diagram](architecture.png)

* A front-end web app in [Python](/vote) or [ASP.NET Core](/vote/dotnet) which lets you vote between two options
* A [Redis](https://hub.docker.com/_/redis/) or [NATS](https://hub.docker.com/_/nats/) queue which collects new votes
* A [.NET Core](/worker/src/Worker), [Java](/worker/src/main) or [.NET Core 2.1](/worker/dotnet) worker which consumes votes and stores them in…
* A [Postgres](https://hub.docker.com/_/postgres/) or [TiDB](https://hub.docker.com/r/dockersamples/tidb/tags/) database backed by a Docker volume
* A [Node.js](/result) or [ASP.NET Core SignalR](/result/dotnet) webapp which shows the results of the voting in real time


Notes
-----

This application is meant to represent Uffizzi's capabilities - to run any service definable in docker-compose in an ephermal preview environment.

Uffizzi is a cross-platform, open source Preview Environment tool.  The example here is with Github and Github Actions but it is designed to work with any VCS, Container Registry, and CI provider.  

Uffizzi provides back end preview envrionments that pair well with Vercel, Netlify and other Front End platforms that enable Previews.

Questions, concerns, issues, feature requests - please join our fast growing [community](https://uffizzi.slack.com/join/shared_invite/zt-ffr4o3x0-J~0yVT6qgFV~wmGm19Ux9A#/shared-invite/email) on Slack.  
