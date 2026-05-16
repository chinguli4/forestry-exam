# 숲가꾸기 사업 품질·안전 오류탐지 경진대회

산림청 신규 담당자 대상으로 현장 사진·행정서류의 품질·안전 오류를 찾아내는 능력을 측정하는 브라우저 기반 경진대회 시스템입니다.

---

## 🖥️ 시험 응시

👉 **[시험 시작하기](https://chinguli4.github.io/forestry-exam/)**

- 제한시간: **90분** (manifest.json에서 변경 가능)
- 문제 구성: **사진 10장 + 문서 10세트**
- 답안은 브라우저에 자동 저장 → 제출 시 **CSV 파일 다운로드** → 담당자에게 파일 전송

---

## 📋 채점 기준

| 평가 항목 | 배점 |
|---|---:|
| 핵심 문제 발견 | 3점 |
| 근거 및 이유 | 2점 |
| 품질·안전 영향 설명 | 2점 |
| 조치 판단 선택 | 2점 |
| 추가자료 요구 | 1점 |
| **문제당 합계** | **10점** |

사진 10문제(100점) + 문서 10문제(100점) = **총 200점 만점**

---

## 🗂️ 문제 추가 방법 (출제자용)

### 사진 문제 (JPG)

1. JPG 파일을 `questions/photos/` 폴더에 저장  
   → 파일명 규칙: `P01.jpg`, `P02.jpg` … (두 자리 번호)

2. `manifest.json`에 항목 추가:
   ```json
   { "id": "P01", "type": "photo", "file": "questions/photos/P01.jpg", "label": "사진 01" }
   ```

### 문서 문제 (PDF)

1. PDF 파일을 `questions/docs/` 폴더에 저장  
   → 파일명 규칙: `D01.pdf`, `D02.pdf` …

2. `manifest.json`에 항목 추가:
   ```json
   { "id": "D01", "type": "doc", "file": "questions/docs/D01.pdf", "label": "문서 01" }
   ```

### 시간·문제 수 변경

`manifest.json`의 `duration_minutes` 값을 수정하세요.

---

## ⚙️ GitHub Pages 설정 순서

1. 이 저장소를 GitHub에 push
2. `Settings → Pages → Source: Deploy from branch` → `main` / `(root)` 선택
3. 사진(JPG)·문서(PDF) 파일을 해당 폴더에 추가 후 push
4. 위 README의 **시험 시작하기** 링크를 실제 GitHub Pages URL로 수정

---

## 📁 폴더 구조

```
├── index.html              ← 시험 화면 (수정 불필요)
├── manifest.json           ← 문제 목록·시간 설정 (출제자 편집)
├── questions/
│   ├── photos/             ← JPG 사진 문제 (P01.jpg ~ P10.jpg)
│   └── docs/               ← PDF 문서 문제 (D01.pdf ~ D10.pdf)
└── README.md
```

---

## ⚠️ 운영 주의사항

- 실제 사업장·개인정보·차량번호가 포함된 사진은 반드시 **익명화** 후 사용
- 시험 중 답안은 브라우저 localStorage에 자동 저장됨 (탭 닫아도 복원)
- 제출된 CSV 파일을 공유폴더 또는 이메일로 수거하여 채점
- 로컬 테스트 시: `python -m http.server` 후 `http://localhost:8000` 접속
