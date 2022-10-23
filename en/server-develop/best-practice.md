> Provide best practice solutions for developers to refer to

**1. Divide the interface development into two parts**

---

### Part 1: Obtaining various authorization `code` operations

> Since various authorized `code` will be updated and obtained regularly, this part of the work is developed as a separate part, and the various authorized `code` is stored in `redis` `mysql`, etc. for separate storage. for easy access to other uses.

!> Please get the one-click deployment code in the development acceleration, which supports `Alibaba Cloud Function Computing (FC)` and docker method for fast one-click deployment.

---

### Part II: Operating user resources and other resource-related business interfaces

> Place this part of the code development in the business code. When you need to use various authorization `code`, obtain it from `redis` `mysql` and other locations, so that the authorization `code` can be kept up to date.

![](../images/20220716042036.jpg ':size=500')

!>We provide `docker` one-click deployment in [Development Acceleration](/#/server-develop/develop-speed-up ':ignore'), and <a href="https://fcnext.console.aliyun .com/overview" target="_blank">Alibaba Cloud Function Computing (FC)</a> deployment method and open source code.
