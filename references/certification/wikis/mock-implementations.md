# Mock Implementations

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Mock-Implementations](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Mock-Implementations)
**Slug:** `Mock-Implementations`

---

# Mock Bank

The latest published version of the mock bank source code can be found on the [GitHub - Mock Bank](https://github.com/OpenBanking-Brasil/applications-exemplo). We note that although this code is open source it still holds a few dependencies with AWS products, making the local execution not straightforward. We also note that the version published on this page might not be completely up to date with the Mock Bank application that is executed by the Central Structure.

The main priority of the initial structure is to create a service that can act as a Mock Bank for TPPs to test their implementations. A complete service requires networking components, security components, resilient databases, public trustworthy certificates, etc. All of which can be provided as an infrastructure as a service provider, like AWS, where possible, the services leveraging AWS cloud services with a minimum of additional components being manually constructed.

The developed components consist of:

- AWS IAM (Security and Policy Enforcement)
- AWS API Gateway (Networking)
- AWS Application Load Balances (Networking)
- AWS Lambda (Compute)
- AWS PostGresRDS (Persistence) 

Inside the [GitHub repository](https://github.com/OpenBanking-Brasil/applications-exemplo/tree/initial-os-drop) is a Bank Swagger that contains a wrapper which is used to generate Java classes from the swagger schema, a [Micronaut](https://micronaut.io/) microservice tier designed to run as a AWS lambda function, and an [Open Source OIDC provider](https://github.com/panva/node-oidc-provider) which has extensive [documentation](https://github.com/panva/node-oidc-provider/blob/main/docs/README.md) that a bank can use to configure any sort of Open ID Connect configuration. In addition, a complete working example running an OIDC Provider locally with [end to end set-up instructions and configurations is also available](https://github.com/panva/node-oidc-provider-example).

For the Micronaut project, this can be compiled to work into other hosting infrastructures, please refer to the Micronaut documentation if you wish to do so. The Micronaut lambdas have some coverage for unit testing which is always being improved, allowing the execution of unit testing over the APIs that it exposes. 

For participants looking to develop a solution to run locally, these components can be made to work with any API Gateway and/or infrastructure provider, however, given the massive range of potential suppliers, services, providers, this support for each bank implementation will not be provided by the Conformance Suite Project Team. 

If you wish to use the [Open Source OIDC provider](https://github.com/panva/node-oidc-provider/blob/main/docs/README.md) please do consider sponsoring the project as additional support is available.

The Conformance Suite do wish to deploy an end-end solution that can run on a local machine, however, given the existing priorities and timelines, this still stands as aspirational. 



---

*Conteúdo baixado em 16/09/2026, 15:38:11*
