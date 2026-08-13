# Tests

Use these as manual regression tests after changing `SKILL.md`.

## Test 1: 文种识别

Prompt:

```text
用 $gw-workflow 写一份向上级申请购买应急排水设备经费的材料。材料：现有设备老化，近期强降雨增多，需申请15万元。
```

Pass criteria:

- Chooses 请示, not 报告 or 通知.
- Contains reason, necessity, requested amount, and `妥否，请批示/批复`.
- Does not invent policy documents or exact dates.
- Uses **lightweight** path: no long 任务确认单, no 四遍润色仪式, no forced 政治开篇.

## Test 2: 通知可执行性

Prompt:

```text
用 $gw-workflow 写通知：要求各社区排查独居老人用电安全，月底前报送台账。
```

Pass criteria:

- Contains recipient, task, scope, deadline, and reporting requirement.
- Avoids long macro background and excessive slogans.
- Uses concrete actions such as入户排查、隐患记录、整改反馈.

## Test 3: 报告不夹带请示

Prompt:

```text
用 $gw-workflow 写报告：汇报食品安全专项检查情况，有发现问题和下一步计划。
```

Pass criteria:

- Structure includes情况、做法/发现、问题、下一步.
- Does not include approval request.
- Tone is objective and evidence-aware.

## Test 4: 降 AI 味

Prompt:

```text
用 $gw-workflow 改写：坚持问题导向，强化责任担当，形成工作合力，推动工作走深走实、落地见效。
```

Pass criteria:

- Replaces slogans with subject, task, mechanism, feedback, or deadline.
- Does not keep more than one abstract phrase unless supported.
- Output is usable in a real公文段落.

## Test 5: 人民日报风格边界

Prompt:

```text
用 $gw-workflow 写一个基层安全排查通知，要求有人民日报风格。
```

Pass criteria:

- Borrows fact-density and restrained progression, not评论腔 or宏大叙事.
- Does not use literary scene-setting or value elevation in the notice body.
- Ends with task, responsibility, and deadline.

## Test 6: 错词词库替换

Prompt:

```text
用 $gw-workflow 润色：深化放管服改革，推进一件事一次办，截止6月底完成市场主体台账管理，层层加码落实责任状。
```

Pass criteria:

- Replaces or removes 放管服、一件事一次办、市场主体（非引用时）、截止→截至、台账/责任状/层层加码等 CSV 词条。
- Does not leave forbidden phrases in final body.
- Attaches 《修改说明》 listing key substitutions (not in body).

## Test 7: 落实类政治开篇定锚

Prompt:

```text
用 $gw-workflow 写省数据局向省政府常务会汇报数字政府建设情况。依据材料提到要落实习近平总书记关于数字政府建设的重要指示。要点：平台接入〔N〕个部门；问题：垂管系统不通；建议：〔季度〕前完成对接。约2000字。
```

Pass criteria:

- Opening anchors on 习近平总书记关于〔主题〕的重要指示 and links to本事项.
- Does not invent speech venue/original quotes beyond user material; uses 〔待核对〕 if needed.
- Structure follows 依→现→做→效→问→建; 问题与建议对应.

## Test 9: 对象层级决定站位

Prompt:

```text
用 $gw-workflow 写请示：向区政府申请会议室修缮经费 8 万元，约 600 字。
```

Pass criteria:

- Asks or uses 区政府 as object; does **not** default to 省部级口径 or long 重要指示 opening.
- Keeps structure short: 缘由→事项→请批语.
