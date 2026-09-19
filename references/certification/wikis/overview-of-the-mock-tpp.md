# Overview of the Mock TPP

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Overview-of-the-Mock-TPP](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Overview-of-the-Mock-TPP)
**Slug:** `Overview-of-the-Mock-TPP`

---

[[_TOC_]]

[This page is also available in Portuguese.](https://gitlab.com/obb1/certification/-/wikis/Vis%C3%A3o-geral-do-Mock-TPP)

# Objective of the Mock TPP

The Mock TPP has been designed and created by the Conformance Suite team to be both a tool to support the execution of tests of Authorisation Servers (FAPI OP) and a tool to support TPPs in building their own fully functional solution. The Mock TPP is provided with a fully Open Source Code that can be easily executed into a local machine.

On this page, we point both where one can find the source code of the Mock TPP and also how to quickly execute it locally in order to run tests against an existing Authorisation Server registered on the Sandbox Directory.

# Mock TPP Source Code

The source code for the Mock TPP is hosted on the [Open Finance Applications Example Repo](https://github.com/OpenBanking-Brasil/applications-exemplo).

In the Open Finance Sandbox Directory, you can find the Mock TPP Software Statement by going [here.](https://web.sandbox.directory.openbankingbrasil.org.br/organisations/74e929d9-33b6-4d85-8ba7-c146c867a817/softwareStatements/7218e1af-195f-42b5-a44b-8c7828470f5a/softwareStatementView)

The Mock TPP is currently being improved by the conformance suite team, however, if you would like to contribute to developing this tool, feel free to raise any P.R. against the repository. Similarly, if you have any suggestions of improvement or if you experience any issues on executing the solution, please raise an issue at the [Conformance Suite Issues Page](https://gitlab.com/obb1/certification/-/issues)

# Quick Start - Running the Mock TPP locally

## What do you need to run:

Docker

MongoDB

Vue

NPM (node package manager)

Node v16 (preferably use this one)

To help with the start we have also recorded a [Quick Start 6 Minutes video](https://youtu.be/bq3GfShkO_A) showing the end-to-end process of executing the Mock TPP

## First time set-up

**(1) Add a local DNS entry in your hosts file:**

**To be able to successfully run the Mock TPP locally, you need to add a DNS entry to your localhost.**

**For a MacOS:**

1. Open a terminal
2. Type: sudo nano /private/etc/hosts
3. Enter your password

**For a Windows 8/10:**

1. Press the Windows key.
2. Type Notepad in the search field.
3. In the search results, right-click Notepad and select Run as administrator.
4. From Notepad, open the following file:

c:\\Windows\\System32\\Drivers\\etc\\hosts

**After opening the hosts file:**

4. You should see your current hosts configuration. Scroll down with your keys until you reach the 127.0.0.1 part and go right just after the 'localhost'.
5. You should add the following entries in your hosts file:

```
127.0.0.1   tpp.localhost
127.0.0.1   mongo1
127.0.0.1   mongo2
127.0.0.1   mongo3
```

6. Save the file: Press "Ctrl + O" to write and "Ctrl + X" to exit on MacOS or just save normally on Windows

In the end, it should look like the picture below (example for a Mac):

![image](uploads/dd6fccbec47afd20ec94333d3b1b08e1/image.png)

**(2) Install the necessary packages:**

Inside the tpp-payments-client folder, open a terminal window and run

```
npm install
```

This will install all the necessary packages

**(3) Execute the Mock TPP:**

Run Docker, after that, open a terminal window and run:

```
docker-compose up
```

Now, inside the applications-exemplo/tpp-payments-client folder, run the following command:

```
npm run start
```

_This will execute a batch script that runs both the front-end and the backend together_

If you want to run them separately, open two terminal windows and run:

Backend:

```
DEBUG=tpp* node index.js
```

Frontend:

```
npm run serve
```

**(4) Allowing your browser to execute the code:**

- After compiling it successfully, open a browser window to https://tpp.localhost and your browser will prompt to ask if you trust this website - press yes.

**(5) Opening the Mock TPP initial screen:**

- Open a window to https://tpp.localhost:8080/ and you'll be able to select if you want to Customer Data or Payments

## Executing the Mock TPP normally

If you've went through the previous setup before, you just need to run the following command inside the tpp-payments-client folder:

```
npm run start
```

This will execute the Mock TPP

# Mock TPP Configuration

The Mock TPP comes populated with an existing set of credentials for an S.S. that is registered on the Sandbox environment. The user may opt to update these credentials together with a few operational variables before executing the Mock TPP to make sure that it is going to use credentials that have been set to work against a given implementation.

The configuration view is divided in:

- Authorization and Message Settings
- Software Statement Settings
- Mock TPP Settings

### Updating Certificates

You can add your own certificates by pressing the "Configurations" button in the home view and then going to "Software Statement settings"

![image](uploads/9c1df2b244dec555eb9e697fe65d0363/image.png)

The Mock TPP expects both the private and public keys of the Signing (BRSEAL) and Transport (BRCAC) certificates and also the Certificate Authority file

- ca.pem
- signing.key
- signing.pem
- transport.key
- transport.pem

When updating the certificates on the configuration file, make sure you use the same names when uploading them.

![image](uploads/8c2b4a071d34abbde199ca758a447bc0/image.png)

![image](uploads/c3fd4bedf90cfcb58ca0a17e90f7d6d0/image.png)

### Configuring other parameters

Every configuration can be changed in the Configurations menu. The Mock TPP was created to be able to be executed and ran by any registered institution in the Directory.

You can change the client details and app details to what you wish to test

![image](uploads/8d98f081f72e9a82ef8ecef5008f1e1a/image.png)

---

*Conteúdo baixado em 16/09/2026, 15:38:15*
