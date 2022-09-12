---
title: "Linting Proto Files With Buf"
description: "Using a linter on your Protobuf sources enables you to enforce consistency and keep your API definitions in line with your chosen best practices."
aliases: ["posts", "articles", "blog", "showcase", "docs"]
date: 2022-09-11T18:27:23+05:30
author: "themayurkumbhar"
tags: ["linting", "protobuf", "buf", "ci", "gitlab"]
draft: false
---

Recently, I had the chance to work on the proto files for one of my projects to define the contract for a service. Since this was a brand-new service, I had to set it up from scratch and learned how to write and format the proto files using best practices.
> What is proto? read more about [protocol bufferes](https://developers.google.com/protocol-buffers)

There are different tools available for linting the proto files some of them are
1. [protoc-gen-lint]()
2. [prototool]()
3. [buf](https://github.com/bufbuild/buf) - 
we have used the `buf` as a proto linter. Follow [this](https://docs.buf.build/installation) for installation of buf.

## What is buf?
The buf CLI is a tool for working with Protocol Buffers. It has a variety of supported functions such as **lint, breaking changes detection, formatter, etc.**

## Format your protos

To improve readability and have standard formatting enabled across teams, buf provides the **auto-formatting** on proto files. This enables the files to be formatted correctly and with following the standards.

Use the following command to format your files.

```bash
buf format
```

This will produce any violations in formatting to the console. 

To auto-format the files **in-place** with the difference in file changes, use the below command.
```bash
buf format -w --diff
```


## Detect code style checks

**Linter** - A static code analysis used to flag programming errors, bugs, stylistic errors, and suspicious constructs.


For proto files, it's no different, to verify the new changes adhere to proto standards use the **buf linter**.
```bash
buf lint /path/to/proto/files/
```
This will produce any errors, warning to console if there are any violations in writing proto files. You can analyze and update the protofiles according to standard rules.

### Automatically lint with GitLab CI pipeline

Whenever there is a change in your repository, your CI pipeline will automatically run `buf lint` to check for any violations.

To check add the below code snippet to the `.gitlab-ci.yml`

```yaml
stages:
  - lint

lint:
  stage: lint
  image: 
    name: bufbuild/buf:1.7.0
    entrypoint: [""]
  script:
    - buf lint
```

## buf configuration rules

buf supports three categories of rule configurations.
1. `MINIMAL`
2. `BASIC`
3. `DEFAULT`

By default, buf has `DEFAULT` linting configuration which has below details.

```yaml
version: v1
lint:
  use:
    - DEFAULT
breaking:
  use:
    - FILE
```
Use `buf mod init` to generate `DEFAUTL` configuration rules for your project.

You can update this file with different rules as per the requirements.
```yaml
 version: v1
 lint:
   use:
     - DEFAULT
   except:
     - PACKAGE_VERSION_SUFFIX
     - FIELD_LOWER_SNAKE_CASE
     - SERVICE_SUFFIX
   ignore:
     - google/type/datetime.proto
 breaking:
   use:
     - FILE
```

Hope this article gave understanding of how to use `buf` tool for **formatting, linting** your proto files. Happy learning!
