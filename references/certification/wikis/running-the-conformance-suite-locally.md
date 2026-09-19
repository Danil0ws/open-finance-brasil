# Running the conformance suite locally

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Running-the-conformance-suite-locally](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Running-the-conformance-suite-locally)
**Slug:** `Running-the-conformance-suite-locally`

---

## Overview

The Conformance Suite is a completely Open Source tool and its source code is located in [the Conformance GitLab Repository](https://gitlab.com/obb1/certification/-/tree/master), with the version present on the [Conformance Suit](https://web.conformance.directory.openbankingbrasil.org.br/) being a hosted deployment of this source code.

As the CS basically simulates a TPP driven by a set of configurations and a series of tests, there's no restriction to which Authorization Server (FAPI-OP) the CS can be pointed at. This also means that the CS can be executed against both production and pre-production servers without restrictions. 

In the process of interacting with a Server, the CS will log a lot of the results and keys that were used in this process, which, although ok for pre-production, is not intended for a production execution as a lot of sensitive data might be exposed. With this idea in mind, although pointing the deployed version of the CS to a production A.S. is possible, it might put at risk of exposing this sensible data. For this reason, when executing the CS against a production server we strongly recommend that this is done with a local version of the CS, which is the main objective of this guide.

## Running the suite locally, in order to run tests.

The conformance suite is a Java web application, built with Spring Boot, although no understanding of Spring Boot is necessary to work on the test suite itself. The suite uses MongoDB as a backend. Luckily we can leverage *docker compose* to run this locally, quite trivially. 

The main repository for the conformance suite can be found in the [gitlab repository](https://gitlab.com/obb1/certification/-/tree/master). 

Note that this Conformance Suite shares its core code with the OpenID Foundation's FAPI Conformance Suite, which is available [here](https://gitlab.com/openid/conformance-suite)

In order to simply spin up the conformance suite, we first need to build the application. This is done using Apache Maven. If you have Maven installed, you can simply run

    $ mvn clean package

If you do not have Maven installed, you can use docker compose. 
First you should install [Docker for your OS](https://docs.docker.com/engine/install/) and then run the local docker application.

After that, use this command to build the application.

    $ docker-compose -f builder-compose.yml up

Once this package is built, we can simply run

    $ docker-compose up

![image](uploads/9027cfd23ceb3d4093c8f70313479cc1/image.png)

And the application is available at https://localhost:443

![image](uploads/3199fb5bfb94140020a8d1b5cf171df6/image.png)

Note that there is a self-signed certificate used for HTTPS, and your browser will complain about this. This is fine.

## Running the suite with a debugger.

There are a number of docker-compose files for running the service locally, and allowing us to attach a Java debugger. 

    $ docker-compose -f docker-compose-dev.yml up

or

    $ docker-compose -f docker-compose-dev-mac.yml up

And the application is available at [https://localhost:8443](https://localhost:8443)

Will both spin up the entire stack, and allow you to attach a Java debugger to port localhost:9999

Alternatively, for a more rapid development workflow, we can opt to run only some of the services with docker-compose, and have the conformance suite run in our IDE, such that code changes will be immediately reflected in the application.

    $ docker-compose -f docker-compose-dev-mac-nodocker.yml up

Will bring up the MongoDB server and an Apache httpd reverse proxy, allowing us to run the application in our IDE. How this works will vary from IDE to IDE. To do this in Intellij, run the  class net.openid.conformance.Application in your IDE. You should edit the generated run configuration to add the mongodb url: 

    -Dspring.data.mongodb.uri=mongodb://127.0.0.1:27017/test_suite

We can stop and start this at will. The application ships with a library called spring-boot-devtools, which means we don't have to stop and re-start the application with every change. Merely re-compiling a class will trigger a reload. This makes for a fairly fast change-compile-test development feedback loop.

## Running the Conformance Suite locally with IntelliJ IDEA

1 - After cloning the repository, open the project with IntelliJ

2 - Open the file src/main/java/net/openid/conformance/Application

3 - Look for the "play" button that is just to the left of the line of code that says `public class Aplication`

4 - Click it with your right mouse button and select the option "Modify Run Configuration..."

5 - In the new window that pops up, click on "Modify options" and then "Add VM options"

6 - Fill "VM options" with:

```-Dfintechlabs.devmode=true -Dspring.data.mongodb.uri=mongodb://127.0.0.1:27017/test_suite -Dfintechlabs.external_url_override=https://www.heenan.me.uk -Dfintechlabs.base_url=https://localhost.emobix.co.uk:8443```

7 - Start up Docker in your terminal:

```docker-compose -f docker-compose-dev-mac-nodocker.yml up```

8 - Run the Application

9 - Now, the application is ready to be used in the address `https://localhost:8443/`

---

*Conteúdo baixado em 16/09/2026, 15:38:33*
