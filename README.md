# ZombieUp

Only Up!에서 모티브를 얻어, 장애물을 오르고 뛰어 정상까지 가는 3D 플랫포머입니다.

- **기간:** 2025.05.25 – 2025.06.09 (약 2주)
- **인원:** 1인 개발 · 수업 과제
- **환경:** Unity 2022.3, C#, CharacterController, Cinemachine, Timeline

## 조작

| 입력 | 동작 |
| --- | --- |
| WASD | 이동 |
| Shift | 달리기 |
| Space | 점프 / 벽 앞에서 등반 |
| 마우스 | 시점 회전 |
| Alt (누른 채) | 둘러보기 |
| 우클릭 | 슬로 모션 |

정상에 도착하면 컷씬과 함께 클리어 시간이 표시됩니다.

## 주요 구현

- **클라이밍 (루트 모션)** — 장애물 윗면 높이로 점프 · 등반 · 등반 불가를 구분하고, 등반은 루트 모션으로 처리. Animator가 자식 모델에 있어 `OnAnimatorMove`에서 이동량을 플레이어 루트로 넘김
- **낙하 · 기상** — 떨어진 높이를 재서 낙하 동작과 기상을 재생. 기상 처리를 별도 컴포넌트로 분리해 클라이밍과 낙하가 함께 쓰고, 이동 입력이 들어오면 생략
- **카메라** — 걷기 · 달리기에 따라 Cinemachine FreeLook 거리를 조절하고, Alt로 둘러본 뒤 원래 시점으로 복귀
- **게임 흐름** — 타이머, 정상 도착 시 Timeline 컷씬, 클리어 화면

## 스크립트 위치

```
Assets/2 Script/
├── Player/   PlayerMovement, PlayerClimb, RootMotionMover, PlayerFall, StandUpHandler, 카메라
├── UI/       GameManager, GameTimer, MainMenuUI, ClearScreen
├── FinishEvent.cs
└── JumpPad.cs
```
