
# Laravel SSR website

> [!TIP]
> To deploy this project using **GUI-based flow**, navigate to [console](https://console.stacktape.com/create-new-project/git-project-using-console?name=my-stacktape-app&repositoryType=public&repositoryUrl=https://github.com/stacktape/starter-laravel-ssr-website)

-   simple Server-side rendered [Laravel](https://laravel.com/) application.
-   The project uses a [Web Service](https://docs.stacktape.com/compute-resources/web-services/) to run the Laravel app.
- This project includes a pre-configured [stacktape.yml configuration](stacktape.yml).
The configured infrastructure is described in the [stack description section](#stack-description)

## Pricing

- Fixed price resources:

  - **Web service** (~$0.012/hour, ~$9/month)

- There are also other resources that might incur costs (with pay-per-use pricing). If your load won't get high, these costs will be close to $0.

## Prerequisites

1. **AWS account**. If you don't have one, [create new account here](https://portal.aws.amazon.com/billing/signup).

2. **Stacktape account**. If you don't have one, [create new account here](https://console.stacktape.com/sign-up).

3. **Stacktape installed**.

  <details>
  <summary>Install on Windows (Powershell)</summary>

  ```bash
  iwr https://installs.stacktape.com/windows.ps1 -useb | iex
  ```

  </details>
  <details>
  <summary>Install on Linux</summary>

  ```bash
  curl -L https://installs.stacktape.com/linux.sh | sh
  ```

  </details>
  <details>
  <summary>Install on MacOS</summary>

  ```bash
  curl -L https://installs.stacktape.com/macos.sh | sh
  ```

  </details>
  <details>
  <summary>Install on MacOS ARM (Apple silicon)</summary>

  ```bash
  curl -L https://installs.stacktape.com/macos-arm.sh | sh
  ```

  </details>




## 1. Generate your project
To initialize the project, use

```bash
stacktape init --starterId laravel-ssr-website
```




## 2. Deploy your stack

The deployment will take ~5-15 minutes. Subsequent deploys will be significantly faster.

<details>
<summary>Deploy from local machine</summary>

<br />

The deployment from local machine will build and deploy the application from your system. This means you also need to have:
- Docker. To install Docker on your system, you can follow [this guide](https://docs.docker.com/get-docker/).

<br />

To perform the deployment, use the following command:

```bash
stacktape deploy --projectName <<project-name>> --stage <<stage>> --region <<region>>
```

`stage` is an arbitrary name of your environment (for example **staging**, **production** or **dev-john**)

`region` is the AWS region, where your stack will be deployed to. All the available regions are listed below.

`projectName` is the name of your project. You can create it in the console or interactively using CLI.

<br />

| Region name & Location     | code           |
  | -------------------------- | -------------- |
  | Europe (Ireland)           | eu-west-1      |
  | Europe (London)            | eu-west-2      |
  | Europe (Frankfurt)         | eu-central-1   |
  | Europe (Milan)             | eu-south-1     |
  | Europe (Paris)             | eu-west-3      |
  | Europe (Stockholm)         | eu-north-1     |
  | US East (Ohio)             | us-east-2      |
  | US East (N. Virginia)      | us-east-1      |
  | US West (N. California)    | us-west-1      |
  | US West (Oregon)           | us-west-2      |
  | Canada (Central)           | ca-central-1   |
  | Africa (Cape Town)         | af-south-1     |
  | Asia Pacific (Hong Kong)   | ap-east-1      |
  | Asia Pacific (Mumbai)      | ap-south-1     |
  | Asia Pacific (Osaka-Local) | ap-northeast-3 |
  | Asia Pacific (Seoul)       | ap-northeast-2 |
  | Asia Pacific (Singapore)   | ap-southeast-1 |
  | Asia Pacific (Sydney)      | ap-southeast-2 |
  | Asia Pacific (Tokyo)       | ap-northeast-1 |
  | China (Beijing)            | cn-north-1     |
  | China (Ningxia)            | cn-northwest-1 |
  | Middle East (Bahrain)      | me-south-1     |
  | South America (São Paulo)  | sa-east-1      |

</details>
<details>
<summary>Deploy using AWS CodeBuild pipeline</summary>

<br />

Deployment using AWS CodeBuild will build and deploy your application inside [AWS CodeBuild pipeline](https://aws.amazon.com/codebuild/). To perform the deployment, use

```bash
stacktape codebuild:deploy --stage <<stage>> --region <<region>> --projectName <<project-name>>
```

`stage` is an arbitrary name of your environment (for example **staging**, **production** or **dev-john**)

`region` is the AWS region, where your stack will be deployed to. All the available regions are listed below.

`projectName` is the name of your project. You can create it in the console or interactively using CLI.

<br />

| Region name & Location     | code           |
  | -------------------------- | -------------- |
  | Europe (Ireland)           | eu-west-1      |
  | Europe (London)            | eu-west-2      |
  | Europe (Frankfurt)         | eu-central-1   |
  | Europe (Milan)             | eu-south-1     |
  | Europe (Paris)             | eu-west-3      |
  | Europe (Stockholm)         | eu-north-1     |
  | US East (Ohio)             | us-east-2      |
  | US East (N. Virginia)      | us-east-1      |
  | US West (N. California)    | us-west-1      |
  | US West (Oregon)           | us-west-2      |
  | Canada (Central)           | ca-central-1   |
  | Africa (Cape Town)         | af-south-1     |
  | Asia Pacific (Hong Kong)   | ap-east-1      |
  | Asia Pacific (Mumbai)      | ap-south-1     |
  | Asia Pacific (Osaka-Local) | ap-northeast-3 |
  | Asia Pacific (Seoul)       | ap-northeast-2 |
  | Asia Pacific (Singapore)   | ap-southeast-1 |
  | Asia Pacific (Sydney)      | ap-southeast-2 |
  | Asia Pacific (Tokyo)       | ap-northeast-1 |
  | China (Beijing)            | cn-north-1     |
  | China (Ningxia)            | cn-northwest-1 |
  | Middle East (Bahrain)      | me-south-1     |
  | South America (São Paulo)  | sa-east-1      |

</details>
<details>
<summary>Deploy using Github actions CI/CD pipeline</summary>

<br />

1. If you don't have one, create a new repository at https://github.com/new
2. Create Github repository secrets: https://docs.stacktape.com/user-guides/ci-cd/#2-create-github-repository-secrets
3. Replace `<<stage>>` and `<<region>>` in the .github/workflows/deploy.yml file.
4. `git init --initial-branch=main`
5. `git add .`
6. `git commit -m "setup stacktape project"`
7. `git remote add origin git@github.com:<<namespace-name>>/<<repo-name>>.git`
8. `git push -u origin main`
9. To monitor the deployment progress, navigate to your github project and select the Actions tab

`stage` is an arbitrary name of your environment (for example **staging**, **production** or **dev-john**)

`region` is the AWS region, where your stack will be deployed to. All the available regions are listed below.

`projectName` is the name of your project. You can create it in the console or interactively using CLI.

<br />

| Region name & Location     | code           |
  | -------------------------- | -------------- |
  | Europe (Ireland)           | eu-west-1      |
  | Europe (London)            | eu-west-2      |
  | Europe (Frankfurt)         | eu-central-1   |
  | Europe (Milan)             | eu-south-1     |
  | Europe (Paris)             | eu-west-3      |
  | Europe (Stockholm)         | eu-north-1     |
  | US East (Ohio)             | us-east-2      |
  | US East (N. Virginia)      | us-east-1      |
  | US West (N. California)    | us-west-1      |
  | US West (Oregon)           | us-west-2      |
  | Canada (Central)           | ca-central-1   |
  | Africa (Cape Town)         | af-south-1     |
  | Asia Pacific (Hong Kong)   | ap-east-1      |
  | Asia Pacific (Mumbai)      | ap-south-1     |
  | Asia Pacific (Osaka-Local) | ap-northeast-3 |
  | Asia Pacific (Seoul)       | ap-northeast-2 |
  | Asia Pacific (Singapore)   | ap-southeast-1 |
  | Asia Pacific (Sydney)      | ap-southeast-2 |
  | Asia Pacific (Tokyo)       | ap-northeast-1 |
  | China (Beijing)            | cn-north-1     |
  | China (Ningxia)            | cn-northwest-1 |
  | Middle East (Bahrain)      | me-south-1     |
  | South America (São Paulo)  | sa-east-1      |

</details>
<details>
<summary>Deploy using Gitlab CI pipeline</summary>

<br />

1. If you don't have one, create a new repository at https://gitlab.com/projects/new
2. Create Gitlab repository secrets: https://docs.stacktape.com/user-guides/ci-cd/#2-create-gitlab-repository-secrets
3. replace `<<stage>>` and `<<region>>` in the .gitlab-ci.yml file.
4. `git init --initial-branch=main`
5. `git add .`
6. `git commit -m "setup stacktape project"`
7. `git remote add origin git@gitlab.com:<<namespace-name>>/<<repo-name>>.git`
8. `git push -u origin main`
9. `To monitor the deployment progress, navigate to your gitlab project and select CI/CD->jobs`

`stage` is an arbitrary name of your environment (for example **staging**, **production** or **dev-john**)

`region` is the AWS region, where your stack will be deployed to. All the available regions are listed below.

`projectName` is the name of your project. You can create it in the console or interactively using CLI.

<br />

| Region name & Location     | code           |
  | -------------------------- | -------------- |
  | Europe (Ireland)           | eu-west-1      |
  | Europe (London)            | eu-west-2      |
  | Europe (Frankfurt)         | eu-central-1   |
  | Europe (Milan)             | eu-south-1     |
  | Europe (Paris)             | eu-west-3      |
  | Europe (Stockholm)         | eu-north-1     |
  | US East (Ohio)             | us-east-2      |
  | US East (N. Virginia)      | us-east-1      |
  | US West (N. California)    | us-west-1      |
  | US West (Oregon)           | us-west-2      |
  | Canada (Central)           | ca-central-1   |
  | Africa (Cape Town)         | af-south-1     |
  | Asia Pacific (Hong Kong)   | ap-east-1      |
  | Asia Pacific (Mumbai)      | ap-south-1     |
  | Asia Pacific (Osaka-Local) | ap-northeast-3 |
  | Asia Pacific (Seoul)       | ap-northeast-2 |
  | Asia Pacific (Singapore)   | ap-southeast-1 |
  | Asia Pacific (Sydney)      | ap-southeast-2 |
  | Asia Pacific (Tokyo)       | ap-northeast-1 |
  | China (Beijing)            | cn-north-1     |
  | China (Ningxia)            | cn-northwest-1 |
  | Middle East (Bahrain)      | me-south-1     |
  | South America (São Paulo)  | sa-east-1      |

</details>

## 3. Test your application

After a successful deployment, some information about the stack will be printed to the terminal (**URLs** of the deployed services, links to **logs**, **metrics**, etc.).

- Explore your application at **mainApiGateway -> url**. The URL is printed to the terminal.





## 4. Hotswap deploys
- Stacktape deployments use [AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) under the hood. It
  brings a lot of guarantees and convenience, but can be slow for certain use-cases.

- To speed up the deployment, you can use the `--hotSwap` flag which avoids using Cloudformation.
- Hotswap deployments work only for source code changes (for lambda function, containers and batch jobs) and for content uploads to buckets.
- If the update deployment is not hot-swappable, Stacktape will automatically fall back to using a Cloudformation deployment.
```bash
stacktape deploy --hotSwap --stage <<stage>> --region <<region>> --projectName <<project-name>>
```

## 5. Delete your stack

- If you no longer want to use your stack, you can delete it.
- Stacktape will automatically delete every infrastructure resource and deployment artifact associated with your stack.

```bash
stacktape delete --stage <<stage>> --region <<region>>
```

# Stack description

  Stacktape uses a simple `stacktape.yml` configuration file to describe infrastructure resources, packaging, deployment
  pipeline and other aspects of your project.

  You can deploy your project to multiple environments (stages) - for
  example `production`, `staging` or `dev-john`. A stack is a running instance of an project. It consists of your application
  code (if any) and the infrastructure resources required to run it.

  The configuration for this project is described below.

  ## 1. Resources

  - Every resource must have an arbitrary, alphanumeric name (A-z0-9).
  - Stacktape resources consist of multiple underlying AWS or 3rd party resources.
### 1.1 Web Service

Application runs in web-service resource and is configured as follows:

-   **Packaging** - determines how the Docker container image is built. In this case, we are using `external-buildpack`.
    We are configuring `sourceDirectoryPath`(in our case it is the root of our project) as well as specifying custom
    heroku builder. The builder scans the directory and automatically chooses buildpack to build the image. Built image
    is then pushed to a pre-created image repository on AWS. You can also use
    [other types of packaging](https://docs.stacktape.com/configuration/packaging/#packaging-web-services).

-   [Resources](https://docs.stacktape.com/compute-resources/web-services#resources). The cheapest available resource
    configuration is `0.25` of virtual CPU and `512` MB of RAM.
-   For convenience, automatic CORS is enabled.

You can also configure [scaling](https://docs.stacktape.com/compute-resources/web-services#scaling). New (parallel)
container can be added when (for example) the utilization of your CPU or RAM gets larger than 80%. The traffic is evenly
distributed to all the containers.

```yml
resources:
    webService:
        type: web-service
        properties:
            packaging:
                type: external-buildpack
                properties:
                    sourceDirectoryPath: ./
                    builder: heroku/builder:22
                    buildpacks:
                        - heroku/php
            resources:
                cpu: 0.25
                memory: 512
            environment:
                # Recommended way to store secrets is to use https://docs.stacktape.com/resources/secrets/
                - name: APP_KEY
                  value: base64:mKaPSaWP+f/tbA6sH/FMlvzy8NzaR6nfhW1h08btVHo=
            cors:
                enabled: true
```
