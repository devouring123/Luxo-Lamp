# 💡 Luxo Lamp

**Three.js 3D 인터랙티브 픽사 램프 구현**

[![Demo](https://img.shields.io/badge/Demo-Live-brightgreen?style=for-the-badge)](https://devouring123.github.io/Luxo-Lamp/)
[![Three.js](https://img.shields.io/badge/Three.js-black?style=for-the-badge&logo=three.js&logoColor=white)](https://threejs.org/)
[![Language](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://github.com/devouring123/Luxo-Lamp)

## 📋 프로젝트 개요

Three.js를 활용하여 픽사의 상징적 캐릭터인 Luxo Jr. 램프를 3D로 재현한 인터랙티브 시뮬레이션입니다. 실시간 관절 제어와 조명 시스템을 구현하여 실제 테이블 램프의 움직임을 사실적으로 표현했습니다.

### 🎯 주요 목표
- **Three.js 마스터**: 고급 3D 웹 그래픽스 기술
- **관절 시스템 구현**: 계층적 변환과 IK/FK 애니메이션
- **실시간 조명**: PBR 기반 사실적 라이팅
- **GUI 인터페이션**: dat.GUI를 통한 직관적 컨트롤

## ✨ 주요 기능

### 🤖 관절형 램프 시스템
- **계층적 구조**: 부모-자식 관계 기반 관절 시스템
- **실시간 제어**: 각 관절의 독립적 회전 조작
- **자연스러운 움직임**: 물리적 제약을 고려한 애니메이션
- **베이스/암/헤드**: 3단계 관절 구조

### 🎨 고급 렌더링 시스템
- **PBR 머티리얼**: 물리 기반 렌더링
- **동적 그림자**: 실시간 그림자 매핑
- **SpotLight**: 램프 헤드에서 나오는 집중 조명
- **Multi-Light Setup**: 환경광 + 포인트라이트 조합

### 🎛️ 인터랙티브 컨트롤
- **dat.GUI 인터페이스**: 실시간 매개변수 조정
- **카메라 컨트롤**: OrbitControls로 자유로운 시점
- **조명 제어**: 빛의 각도와 강도 조절
- **램프 형태 변경**: 암 길이, 관절 각도 실시간 수정

## 🛠️ 기술 스택

| 분야 | 기술 스택 |
|------|-----------|
| **Frontend** | Vanilla JavaScript (ES6+) |
| **3D Engine** | Three.js r150+ |
| **UI Library** | dat.GUI |
| **Controls** | OrbitControls |
| **Math** | Three.js Math Utils |

## 🎨 기술적 구현 세부사항

### 계층적 관절 시스템
```javascript
// 관절 계층 구조 구현
const base = new THREE.Object3D();
const armLower = new THREE.Object3D();
const armUpper = new THREE.Object3D(); 
const head = new THREE.Object3D();

// 계층적 관계 설정
base.add(armLower);
armLower.add(armUpper);
armUpper.add(head);

// 각도 기반 회전 제어
jointBase.rotation.x = THREE.MathUtils.degToRad(angle);
```

### PBR 조명 시스템
```javascript
// SpotLight 구현
const lampLight = new THREE.SpotLight(0xffffff);
lampLight.castShadow = true;
lampLight.angle = THREE.MathUtils.degToRad(30);

// 그림자 매핑 설정
renderer.shadowMap.enabled = true;
renderer.shadowMap.type = THREE.PCFSoftShadowMap;
```

### 프로시져얼 지오메트리
- **BoxGeometry**: 램프 베이스와 관절부
- **CylinderGeometry**: 램프 암과 조인트
- **ConeGeometry**: 램프 헤드 셰이드
- **SphereGeometry**: 전구와 장식 오브젝트

## 🎮 조작법

### 기본 컨트롤
- **마우스 드래그**: 카메라 회전
- **스크롤휠**: 줌 인/아웃
- **GUI 패널**: 실시간 매개변수 조정

### GUI 컨트롤 패널
- **Base Position**: 램프 베이스 위치 (X, Z축)
- **Arm Lengths**: 상/하 암 길이 조정
- **Joint Angles**: 각 관절 회전각 제어
- **Light Settings**: 조명 각도와 헬퍼 표시

## 📊 성능 최적화

### 렌더링 최적화
- **Frustum Culling**: 시야각 외 객체 제거
- **LOD 시스템**: 거리별 디테일 조절
- **Texture Atlasing**: 텍스처 메모리 최적화
- **Shadow Map 해상도**: 동적 품질 조정

### 메모리 관리
- **Geometry 재사용**: 인스턴싱으로 메모리 절약
- **텍스처 압축**: GPU 메모리 효율화
- **가비지 컬렉션**: 불필요한 객체 정리

## 🎨 시각적 특징

### 머티리얼 시스템
- **MeshPhongMaterial**: 광택 있는 금속 질감
- **Color Coding**: 각 부품별 구분되는 색상
- **반사/굴절**: 환경 매핑으로 사실감 증대

### 장면 구성
- **3D Room**: 램프가 놓인 가상 공간
- **장식 오브젝트**: 구체, 사면체, 토러스 등
- **바닥 반사**: 램프 그림자와 반사 효과

## 🌟 데모 및 스크린샷

### [🎮 라이브 데모 체험하기](https://devouring123.github.io/Luxo-Lamp/)

## 🚀 실행 방법

```bash
# 레포지토리 클론
git clone https://github.com/devouring123/Luxo-Lamp.git

# 로컬 서버 실행
python -m http.server 8000
# 또는 Node.js 사용 시
npx serve .

# 브라우저에서 접속
http://localhost:8000
```

## 📈 개발 성과 및 학습 효과

### 기술적 도전과 해결
1. **관절 시스템 구현**
   - 문제: 복잡한 계층적 변환과 제약 조건
   - 해결: Three.js Object3D 부모-자식 관계 활용

2. **실시간 조명 계산**
   - 문제: 다중 조명으로 인한 성능 저하
   - 해결: 적응적 그림자 품질과 LOD 시스템

3. **자연스러운 애니메이션**
   - 문제: 기계적인 움직임 개선
   - 해결: Easing 함수와 물리 기반 보간

### 핵심 학습 성과
- **3D 수학**: 쿼터니언, 오일러각, 행렬 변환
- **컴퓨터 그래픽스**: 조명 모델, 셰이딩, 래스터화
- **Three.js 생태계**: 고급 기능과 최적화 기법
- **UX 디자인**: 직관적 3D 인터페이스 설계

## 🔧 향후 개발 계획

- [ ] **물리 시뮬레이션**: Cannon.js 통합으로 중력/충돌
- [ ] **애니메이션 시퀀스**: 키프레임 기반 자동 동작
- [ ] **VR 지원**: WebXR로 가상현실 경험
- [ ] **음향 효과**: Web Audio API로 몰입감 증대
- [ ] **모바일 최적화**: 터치 제스처와 성능 개선

## 👨‍💻 개발자 정보

**서명교 (devouring123)**  
📧 devouring123@gmail.com  
🔗 [GitHub](https://github.com/devouring123)

---

*"Three.js로 구현한 픽사 스타일 인터랙티브 3D 램프"*