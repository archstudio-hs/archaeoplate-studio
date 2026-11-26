# 함께 쓰는 라이브러리와 AI 모델

이 저장소의 코드는 PolyForm Strict 1.0.0을 따르지만, 아래 구성 요소는 각자의 라이선스를 따릅니다.
빌드할 때 내려받아 `dist/`에 함께 들어갑니다.

## 라이브러리
| 이름 | 용도 | 라이선스 | 출처 |
| --- | --- | --- | --- |
| PDF.js (pdfjs-dist 3.11.174) | PDF 열기·렌더링 | Apache-2.0 | https://github.com/mozilla/pdf.js |
| Tesseract.js 5.1.1, tesseract.js-core | 스케일바·번호 문자 인식(OCR) | Apache-2.0 | https://github.com/naptha/tesseract.js |
| Tesseract 언어 데이터 (eng, kor · 4.0.0_best_int) | OCR 언어 모델 | Apache-2.0 | https://github.com/tesseract-ocr/tessdata_best |
| ONNX Runtime Web 1.31.1 | 브라우저 안 AI 추론 | MIT | https://github.com/microsoft/onnxruntime |

## AI 모델
| 이름 | 용도 | 라이선스 | 원 저작 | 내려받는 곳 |
| --- | --- | --- | --- | --- |
| IS-Net general-use | 자동 누끼 | Apache-2.0 | https://github.com/xuebinqin/DIS | https://github.com/danielgatis/rembg/releases/tag/v0.0.0 |
| MobileSAM 인코더 | 클릭 객체 선택 | Apache-2.0 | https://github.com/ChaoningZhang/MobileSAM | https://github.com/CVHub520/X-AnyLabeling/releases/tag/v0.2.0 |
| SAM 마스크 디코더 | 클릭 객체 선택 | Apache-2.0 | https://github.com/facebookresearch/segment-anything | https://github.com/CVHub520/X-AnyLabeling/releases/tag/v0.2.0 |

모델 파일은 빌드할 때 가중치를 float16으로 바꿔 용량을 절반으로 줄입니다(`scripts/onnx-f16.mjs`). 계산은 float32 그대로라 결과 차이는 무시할 수준입니다(IS-Net 출력 최대 차이 0.001).

## 디자인 참고
- 화면 수치(버튼 높이·모서리 반경·세그먼트 컨트롤)는 Puppertino (MIT, https://github.com/codedgar/Puppertino)를 참고했습니다. 코드는 가져오지 않았습니다.

## 직접 만든 모델
- 도면 선 복원 모델(`src/ai/restore-x2-v2.onnx`, `src/ai/restore-x2-small-v2.onnx`)은 이 저장소 저작자가 직접 학습한 모델로, 저장소 라이선스를 따릅니다. 학습에는 저작자가 정리한 실측도와 『동래 복천동 고분군』 ⅩⅢ~ⅩⅦ 보고서의 벡터 도면을 썼습니다.
