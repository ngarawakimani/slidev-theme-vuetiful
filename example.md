---
theme: ./
clicks: 1
altCover: true 
---

# Bitbucket Pipelines

An integrated CI/CD service built into Bitbucket Cloud

---
layout: big-points
title: Features
titleRow: true
---

- Easy setup
- Integrations
- Deployments

---
layout: big-points
title: Setup....
titleRow: true
---

- Create a yml file `bitbucket-pipelines.yml`
- Enable pipelines

---
title: Example yml file
titleRow: true
---

```js
pipelines:
  pull-requests:
   '**':
    - step:
       name: E2E Tests
       script:
         - pipe: atlassian/ssh-run:0.3.1
           variables:
             SSH_USER: 'root'
             SERVER: $SERVER_IP
             COMMAND: 'cd /projects/wl3api-localdev/wlapi.fh.org && chmod -R 764 test.sh && ./test.sh'
```

---
layout: outro
---

Demo

---
layout: outro
---

Thank you for listening!

Questions?
