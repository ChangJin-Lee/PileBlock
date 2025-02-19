# PileBlock

`PileBlock`은 블럭을 이동시켜 올바른 위치에 블럭을 쌓는 게임입니다.
C++와 블루프린트(BP)를 적절히 사용했습니다.

## 프로젝트 정보

- **프로젝트 기간** : 2024.12.04 ~ 2024.12.12
- **참여 인원** : 1명
- **사용 엔진** : Unreal Engine 5.4
- **플랫폼** : WindowPC

## 주요 기능

### 1. **블럭 삭제**
- 충돌 지점에서 블럭 삭제
- 레이캐스트를 사용하여 블럭 제거
- Boolean 연산을 통한 블럭 제거

참고 자료:
- [Geometry Scripting User Guide](https://dev.epicgames.com/documentationen-us/unreal-engine/geometry-scripting-users-guide-in-unreal-engine)
- [Boolean 연산 YouTube Video](https://www.youtube.com/watch?v=SJ0mEIHRWbE)
- [Boolean 연산 YouTube Video 2](https://www.youtube.com/watchv=Pj-3sYOZEow)

### 2. **블럭 스폰**
- 스폰 위치를 액터로 배치하여 설정
- 랜덤 위치에서 블럭 스폰
- 스폰이 불가능한 위치 판단 및 이동 방향 판정

### 3. **블럭 이동**
- 블럭을 일정 방향으로 이동시키는 로직 구현

### 4. **사용자 입력 처리**
- 프로젝트 세팅에서 입력 액션 및 바인드 설정
- C++ 로직 완성 후 블루프린트에서 Key SpaceBar 로직 실행
- UE5 향상된 입력 시스템 활용

### 5. **UI 만들기**
- 인트로, 로딩, 인게임, 엔드 화면 제작
- 위젯을 통해 층수, 남은 기회 횟수 등 표시
- 블루프린트에 변수 선언 후 위젯에서 사용

### 6. **패배 조건**
- 기회 3번 설정: 블럭을 못 쌓았을 경우 패배 처리

### WBP (Widget Blueprints)

1. **Intro 위젯**
    - 인트로 화면 구현
2. **Loading 위젯**
    - 로딩 화면 구현
3. **In-game 위젯**
    - 층수 표시
    - 남은 기회 횟수 표시
4. **End 화면 위젯**
    - 성공/실패 화면 구현

### 사운드

- 버튼 클릭 시 사운드 재생
- 사운드 에셋 로드 및 재생
    ```cpp
    static ConstructorHelpers::FObjectFinder<USoundBase> ClickSoundAsset(TEXT("/Script/Engine.SoundWave'/Engine/VREditor/Sounds/UI/Click_on_Button.Click_on_Button'"));
    if (ClickSoundAsset.Succeeded())
    {
        ClickSound = ClickSoundAsset.Object;
    }
    ```

### 이벤트 디스패처

- 사용자 입력 처리 및 이벤트 디스패처를 통해 로직 연결

### Spawner

- 스폰 위치를 액터로 배치하여 설정
- 랜덤 위치에서 블럭 스폰
    ```cpp
    float RandomX = FMath::FRandRange(-10.f, 10.f);
    FVector SpawnLocation = FVector(RandomX, RandomY, RandomZ);
    ```
