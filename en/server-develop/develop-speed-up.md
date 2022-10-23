> Quickly realize corresponding business

### Realize the acquisition and automatic update of authorization `code`

1. Use `docker-compose` to deploy, this method can automatically cache data to redis, automatically start proxy server and other functions.
   **For specific `compose` deployment, please refer to:**
   https://github.com/yuanzhibang-tool/docker/tree/main/oapp-code-docker-compose

> The `compose` implements the work of proxy, redis storage and regular update of `access_token` and `ticket`, and will regularly clean up the log to keep the log from taking up too much space

_Note: Please configure the open platform application information you need and add the IP whitelist under the open platform application, otherwise an error will be returned. The logs have been mounted to the `logs` directory. If you have any questions, please check the directory. If developers need to compose their own business, please refer to the `compose` file to adjust._

---

### Supported docker images, please refer to

https://hub.docker.com/u/yuanzhibang

---

Docker image building and `code` update tasks are open source projects, please refer to:

https://github.com/yuanzhibang-tool/docker.git

https://github.com/yuanzhibang-tool/oapp-token-cron-task.git

!>Please pay attention to read the project and the README.md in the directory for faster functional development

---

### Rapid development of business interfaces

**node interface development**
We encapsulate the call to the interface, and `node` develops the `npm` library that encapsulates `node`

https://www.npmjs.com/package/@yuanzhibang/oauth-server

For specific usage instructions, please refer to the open source project and code remarks.

https://github.com/yuanzhibang-tool/oauth-server.git

---

**java,php,python interface development**
We provide a demo, which encapsulates the interface to a certain extent, please refer to use.

https://github.com/yuanzhibang-tool/demo

---

**_demo or the work done by the npm package:_**

1. `js` signature generation

2. Encapsulation calls of all interfaces

3. Interface call supports setting proxy, please refer to unit test code for specific usage

4. Support getting `server_access_token` or `js_ticket` from redis

!>Apes are welcome to provide demo code in other languages, please encapsulate it according to the package of other languages, and provide unit tests. The provided code will follow the MIT protocol.
