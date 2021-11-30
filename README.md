# 볼링 게임 점수판

## 요구 사항
- 최종 목표는 볼링 점수를 계산하는 프로그램을 구현한다. 1단계 목표는 점수 계산을 제외한 볼링 게임 점수판을 구현하는 것이다.
- 각 프레임이 스트라이크이면 "X", 스페어이면 "9 | /", 미스이면 "8 | 1", 과 같이 출력하도록 구현한다.
  - 스트라이크(strike) : 프레임의 첫번째 투구에서 모든 핀(10개)을 쓰러트린 상태
  - 스페어(spare) : 프레임의 두번재 투구에서 모든 핀(10개)을 쓰러트린 상태
  - 미스(miss) : 프레임의 두번재 투구에서도 모든 핀이 쓰러지지 않은 상태
  - 거터(gutter) : 핀을 하나도 쓰러트리지 못한 상태. 거터는 "-"로 표시
- 10 프레임은 스트라이크이거나 스페어이면 한 번을 더 투구할 수 있다.


## 기능 목록

- BowlingController
  - 볼링 점수판 생성 및 진행한다.
- InputView
  - 플레이어를 입력받는다.
  - 각 프레임의 투구를 입력받는다.
- ResultView
  - 각 프레임 별 투구 결과를 출력한다.
- Domain
  - Player
    - 플레이어 이름을 저장한다.
  - Bowling
    - 볼링 게임을 상태를 관리한다.
    - 다음 Pitching 이 있는지 체크한다.
    - 전달받은 Pins (볼링핀) 을 이용하여 볼링을 진행한다.
  - Index
    - 프레임의 인덱스를 관리한다. (1 ~ 10)
  - Pins
    - 사용자가 입력한 쓰러트린 볼링핀 갯수를 관리한다. (0 ~ 10)
    - 볼링 핀을 전달 받아 스트라이크 여부와 스페어 여부를 반환한다.
  - Frame
    - 현재 프레임의 볼링 게임을 수행한 후 현재 프레임 또는 새로운 프레임을 반환한다.
    - 현재 프레임이 종료되어있는지 체크한다.
    - 현재 프레임의 인덱스를 반환한다.
    - NormalFrame : 1 ~ 9 프레임
    - LastFrame : 10 프레임
  - State
    - 현재 상태를 관리하며 볼링핀을 통해 상태를 변경한다.
    - 현재 상태가 종료된 상태인지 체크한다.
    - Ready : 투구를 하지 않은 상태
    - FistBowl : 1회 투구하였으나 스트라이크가 아닌 경우
    - Strike : 1회 투구하여 스트라이크
    - Spare : 2회 투구시에 10개 핀을 쓰러뜨린 경우
    - Miss : 2회 투구하였으나 10개 핀을 모두 쓰러뜨리지 못한 경우