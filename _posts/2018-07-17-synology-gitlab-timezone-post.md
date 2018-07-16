---
title: "시놀로지 GitLab 의 시간대를 한국시간으로 동기화"
date: 2018-07-17 06:20
categories: ssh, gitlab
---

시놀로지에 GitLab 을 처음 설치하면 시간대가 UTC-0 로 설정되었기 때문에 한국 시간과 9시간 차이가 난다.

### 솔루션
1. 시놀로지 패키지 센터에서 GitLab 정지
1. Docker 에서 "비디오 형식" 선택
1. synology_gitlab 을 선택하고 편집을 누른다.
1. 환경탭에서 "+" 버튼을 누른다.
1. 변수명에는 "GITLAB_TIMEZONE", 값에는 "Asia/Seoul" 입력
1. 적용을 누른다.
1. 패키지 센터에서 GitLab 실행
