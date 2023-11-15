# Multi Container Pods

한 Pod에 웹 서버와 로깅 서비스처럼 두 가지 서비스가 필요할 수도 있다. 함께 장착된 웹 서버 인스턴스 당 LOG 에이전트 인스턴스 하나가 필요하다.

두 서비스는 각각 다른 기능을 대상으로 하므로 따로 개발하고 배포하길 원한다. 둘은 같이 스케일업하고 스케일다운 되어야 한다. 그래서 같은 lifecycle을 공유하는 Multi Container Pod가 존재한다.



Multi Container는 한 Pod 내에서 같은 네트워크 공간을 공유한다.

* 서로를 localhost라고 부를 수 있다.
* 서로 같은 storage volumes에 접근한다.
* 그들 사이의 통신이 가능하도록 Volume Sharing이나 Service를 설정하지 않아도 된다.

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
