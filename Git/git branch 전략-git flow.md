# Git Flow

> git flow는 **`feature`**, **`develop`**, **`release`**, **`hotfix`**, **`master`** 5가지의 브랜치를 갖는다.
> 

![스크린샷 2022-07-24 오후 10.45.13(2).png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/695d44de-3618-4993-a6d5-918f994e4f6d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-07-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10.45.13%282%29.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220724%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220724T135853Z&X-Amz-Expires=86400&X-Amz-Signature=866337f79bce8cd150870a9e445bb40e97f2843b63e7b8bb440c01fd1d2e2386&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-07-24%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252010.45.13%282%29.png%22&x-id=GetObject)

1. **main** → ***기준이 되는 브랜치***로 제품을 배포하는 브랜치.
2. **develop** → main에서 시작되는 ***“개발 브랜치"*** 로 개발자들이 이 브랜치를 기준으로 각자 작업한 기능들을 합침.(Merge)
3. **feature** → develop에서 시작되어 단위 기능을 개발하는 브랜치로 ***기능 개발이 완료되면 develop 브랜치에 함침.***
4. **release** → 배포를 위해 ***main 브랜치로 보내기 전에 QA(품질 검사)*** 를 하기 위한 브랜치. (develop에서 생성)
5. **hotfix** → main 브랜치로 배포를 했는데 버그가 생겼을 때 긴급 수정하는 브랜치.

> 💥 ***main***과 ***develop***가 중요한 ***메인 브랜치(항상 존재)*** 이고, 나머지는 필요에 의해 운영하는 브랜치!!!
>
