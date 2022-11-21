## Workflows (작업 흐름)

- 자동화 한 작업 과정을 의미
- 가장 상위 개념
- `.github/workflow` 아래에 위치
- 여러개 생성 가능
- 2가지 정의 필요
  - `on` : "언제 실행" 되는지 ([사용 문법 문서](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions))
  - `jobs` : "어떤 일을 실행"하는지 (아래 상세 설명)

## Jobs (작업)

- 하나의 처리 단위
- workflow는 최소 하나의 job 필요
- job은 기본적으로 동시 실행
  - 필요 시 실행 순서 제어 가능
- `id : 세부 내용` 형태로 표시
  - `runs-on` : 세부 내용의 필수 속성으로, 실행 환경 지정하는 속성

## Steps (단계)

- 여러 명령을 순차적으로 실행할 때 사용
- 각 job은 하나 이상의 step으로 구성
  - `run` : command나 script 실행할 때 사용
  - `uses` : action 실행할 때 사용 (아래 상세 설명)
- `run`과 `uses` 는 YAML문법에서 sequence타입을 사용하므로 앞에 `-`를 붙여야 함

## Actions (액션)

- 빈번하게 반복되는 step을 재사용하기 쉽도록 만들어 놓은 것
- 여러 workflow 간 공유 가능
- [Github Marketplace](https://github.com/marketplace?type=actions)에서는 다른 사람들이 공유한 action 볼 수 있음

---

## 모노레포에서 job에 대한 default working directory 설정
```
  jobId:
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: "./경로 설정"
```
