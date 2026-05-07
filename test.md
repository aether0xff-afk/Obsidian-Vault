| 지표                         | 의미                                                | 해석 방향                                                  |
| -------------------------- | ------------------------------------------------- | ------------------------------------------------------ |
| `no_activity_ratio`        | 자극이 입력되었음에도 활성 branch 또는 trace가 형성되지 않은 샘플의 비율이다. | 값이 높을수록 branch가 시작되지 않는 문제가 크다는 뜻이다.                   |
| `len1_ratio`               | 형성된 branch가 길이 1 수준에서 바로 종료된 비율이다.                | 값이 높을수록 branch collapse가 심하다는 뜻이다.                     |
| `hit_max_ticks_ratio`      | trace가 설정된 최대 tick까지 지속된 샘플의 비율이다.                | 값이 높을수록 branch가 과도하게 오래 유지되는 over-persistence 가능성이 크다. |
| `mean_first_active_tick`   | 첫 활성 branch가 나타난 tick의 평균값이다.                     | 값이 클수록 자극 이후 branch 점화가 늦게 일어났다는 뜻이다.                  |
| `mean_branch_len`          | dominant branch 길이의 평균값이다.                        | 값이 너무 작으면 collapse를, 너무 크면 과도한 지속성을 의미할 수 있다.          |
| `mean_active_window_ticks` | trace가 활성 상태를 유지한 구간의 평균 tick 수이다.                | branch의 평균 지속 시간을 확인하기 위한 지표이다.                        |

| 보정 범주                | 조정 목적                              | 관련 지표                                             |
| -------------------- | ---------------------------------- | ------------------------------------------------- |
| Ignition             | 자극 이후 branch가 시작되지 않는 문제를 완화한다.    | `no_activity_ratio`, `mean_first_active_tick`     |
| Persistence          | branch가 1-step에서 바로 사라지는 문제를 완화한다. | `len1_ratio`, `mean_branch_len`                   |
| Fatigue / inhibition | 과도한 활성 지속과 조기 소멸 사이의 균형을 조절한다.     | `hit_max_ticks_ratio`, `mean_active_window_ticks` |
| Convergence          | trace가 적절한 시점에 종료되도록 조절한다.         | `hit_max_ticks_ratio`, `mean_branch_len`          |