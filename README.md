# inhaler-coach-models

Inhaler Coach 앱의 **실시간 코칭(실험)** 이 내려받는 모델 묶음을 배포하는 저장소입니다.
모델 파일은 저장소가 아니라 [Releases](../../releases)에 올립니다. 릴리스 하나가 묶음 한 버전입니다.

## 앱에 넣는 주소

설정 → 실시간 코칭 → 모델 주소에 아래를 넣고 "업데이트 확인"을 누릅니다.

```
https://github.com/hopekgh/inhaler-coach-models/releases/latest/download/manifest.json
```

`latest`는 가장 최근 릴리스를 가리키므로, 새 릴리스를 올리면 앱에서 업데이트 확인만 하면 됩니다.
앱은 `manifest.json`에 적힌 크기·sha256으로 받은 파일을 검사합니다.

## 묶음 구성 (`dpi_turbuhaler`)

| 파일 | 내용 |
|---|---|
| `manifest.json` | 묶음 버전, 단계 순서·문구, 모델 입력 형식, 파일 크기·sha256 |
| `cap.onnx` | 캡 닫힘/열림 |
| `twist_frame.onnx`, `twist_head.onnx` | 손잡이 왕복(프레임 특징 + 손 골격 + 소리) |
| `seal.onnx` | 마우스피스 물기 |
| `inhale.onnx` | 들이마시기(영상 + 소리) |
| `hand_landmarker.task` | Google MediaPipe 손 추적 모델(Apache-2.0) |

묶음은 [hopekgh/inhaler_coach](https://github.com/hopekgh/inhaler_coach)의 `training_studio/app/mobile_bundle.py`로 내보냅니다.
실기기 점검용 검증 입력(`parity/`)은 실제 촬영 프레임이 들어 있어 여기에 올리지 않습니다.

## 주의

- 교육용 동작 관찰이며 진단·처방이 아닙니다. 흡입 세기·깊이와 약 장전 여부는 판단하지 않습니다.
- 한 사람의 촬영으로 파인튜닝한 시험용(PoC) 모델입니다. 다른 사람·환경에서는 잘 맞지 않을 수 있습니다.
