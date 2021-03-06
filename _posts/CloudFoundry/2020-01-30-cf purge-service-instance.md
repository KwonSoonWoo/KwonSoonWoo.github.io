---
layout: post
title: cf purge-service-instance
category: CloudFoundry
tags:
  - cloudfoundry
  - cf push 에러
  - cf purge-service-instance
  - Could not bind to service
---





cf push 할때 아래와 같은 에러메시지가 뜨면서 push가 안됐음.

```
Could not bind to service ceph-test
Error: Server error, status code: 502, error code: 10001, message: The service broker rejected the request to https://rubyceph.cx-dev.crossent.com/v2/service_instances/e54d5108-3d97-4e0e-bc82-9450f053e26c/service_bindings/5c289e81-e542-4970-b4c8-3566296614f5. Status Code: 404 Not Found, Body: 404 Not Found: Requested route ('rubyceph.cx-dev.crossent.com') does not exist.
```

Cloud Foundry에서 서비스 인스턴스를 먼저 삭제하지 않고 

서비스 브로커를 종료하거나 제거한 경우, 

마켓 플레이스에서 서비스 브로커 또는 서비스 및 계획을 제거 할 수 없다.

개발 환경에서 브로커 작성자는 브로커 배포를 파기하고 

Cloud Controller 데이터베이스를 정리할 방법이 필요하다.



다음 명령은 서비스 브로커에 대한 API 호출을 수행하지 않고 단일 서비스 인스턴스, 

서비스 바인딩 및 해당 서비스 키를 Cloud Controller 데이터베이스에서 삭제한다.



```
cf purge-service-instance <서비스 인스턴스 명>
```

내 경우엔 `ceph-test`가 서비스 인스턴스







---

### Reference

[CloudFoundry Documentation](