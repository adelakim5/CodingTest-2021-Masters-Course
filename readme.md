# 3단계: 루빅스 큐브 구현하기

## 코드 동작

1. 초기 큐브의 모습과 간단한 프롬프트 메시지를 줄바꿈하여 출력한다.
   - 큐브는 큐브의 각 6면을 평면에 펼친 모양으로 출력한다.
   - 윗줄: 큐브의 **윗면**
   - 가운데줄: 큐브의 **왼쪽, 정면, 오른쪽, 뒷면**
   - 아랫줄: 큐브의 **밑면**
2. 사용자가 명령어를 입력한다.
3. 사용자가 명령어를 처음 입력하였을 때의 시간(시작시간)을 저장한다.
4. 입력된 명령어를 parse한다.
   - `'`가 포함된 명령어들의 경우 해당 알파벳의 소문자로 명령어를 변환한다.
5. 입력된 명령어의 길이만큼 각 명령어에 대한 큐브 회전을 수행한다.
   1. 큐브의 여섯면을 각각 2차원배열로 만든다.
   2. 입력된 명령어를 분석한다.
      - 입력된 명령어가 `Q`거나 `Q`를 포함하면? `Q`가 나오기 전에 입력된 명령어들을 차례로 수행한 후 `경과시간, 조작개수, 종료메시지`를 출력하며 종료한다.
        - `Q`를 입력한 시점의 시간(종료시간)을 구한다.
        - 종료시간과 시작시간의 차이를 통해 경과시간을 계산한다.
      - 입력된 명령어가 `S`면? 큐브를 무작위로 섞은 후, 섞은 큐브를 평면으로 펼친 모양으로 출력한다.
        - 큐브를 회전시키는 각 명령어들을 배열에 담는다.
        - 배열에 담긴 명령어를 임의의 수만큼 무작위로 뽑는다.
        - 뽑힌 명령어에 맞는 함수를 호출하여 큐브를 회전시킨다.
      - 입력된 명령어가 명령어가 아니면? `잘못된 입력입니다. 다시 입력해주세요.`를 출력한다.
      - 그 외에는 다음을 수행한다.
   3. 큐브 조작 개수를 하나씩 세어준다.
   4. 명령어에 맞는 함수를 실행한다.
      - 큐브의 윗면/아랫면을 왼쪽 방향으로 회전
      - 큐브의 윗면/아랫면을 오른쪽 방향으로 회전
      - 큐브의 왼쪽면/오른쪽면을 위쪽 방향으로 회전
      - 큐브의 왼쪽면/오른쪽면을 아랫쪽 방향으로 회전
      - 큐브의 정면/뒷면을 시계방향으로 회전
      - 큐브의 정면/뒷면을 반시계방향으로 회전
      - ※ 회전 방향에 따라 각 함수를 실행하되, 회전하는 행/열이 다르므로 `명령어`를 매개변수로 받아 큐브 내 회전시키는 영역을 구분한다.
   5. 입력받은 각 명령어와 함께 회전시킨 큐브를 평면에 펼친 모습으로 출력한다.
      - parse된 명령어라면, parse 전의 명령어로 복귀시켜 출력한다.
   6. (만약 조작개수가 0보다 크고 큐브의 모든 면이 맞춰졌다면) `축하메시지`와 함께 `경과시간, 조작개수, 종료메시지`를 출력하며 종료한다.
      - 큐브가 다 맞춰진 때의 시간(종료시간)을 구한다.
      - 종료시간과 시작시간의 차이를 구해 경과시간을 계산한다.
