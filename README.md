# 📊 ELK 미디어 채널 이용 분석
우리 FISA에서 제공해준 우리은행 카드정보를 활용하여 ELK을 통해 미디어 채널 이용을 분석한 프로젝트입니다.


# 👥팀소개
<div align="center">
  
|신준수|문민경|최소영|장송하|
|:---:|:---:|:---:|:---:|
|[shinjunsuuu](https://github.com/shinjunsuuu)|[Minkyoungg0](https://github.com/Minkyoungg0)|[ottffss1005](https://github.com/ottffss1005)|[jangongha](https://github.com/songhajang)|
|<img width="200" height="250" alt="Image" src="https://github.com/shinjunsuuu.png" />|<img width="200" height="250" alt="Image" src="https://github.com/user-attachments/assets/94f643a0-b74f-42ec-8eb4-e00ffcae4ef1" />|<img width="200" height="250" alt="Image" src="https://github.com/ottffss1005.png" />|<img width="200" height="250" alt="Image" src="https://github.com/user-attachments/assets/36f811b5-e8e9-43f4-b833-b4b9dae40e82" />|
  
</div>

### ❓ELK 스택이란
**ELK Stack**은 로그 및 데이터 분석, 시각화를 위한 오픈소스 기반 통합 플랫폼입니다.  
**Elasticsearch**, **Logstash**, **Kibana**의 머리글자를 따서 ELK라 부르며,  로그 분석, 보안 모니터링, 트랜잭션 추적, 사용자 행동 분석 등에 활용됩니다.
**각 요소별로 하는 역할**

- 🔎 **Elasticsearch**:  
  실시간으로 데이터를 저장하고 검색할 수 있는 분산형 검색 및 분석 엔진입니다.

- 🛠️ **Logstash**:  
  다양한 소스로부터 데이터를 수집하고 변환하여 Elasticsearch로 전달하는 데이터 파이프라인 도구입니다.

- 📊 **Kibana**:  
  Elasticsearch에 저장된 데이터를 시각화하고, 대시보드를 구성할 수 있는 사용자 인터페이스 도구입니다.
### ✅ 왜 ELK 스택을 사용했는가?
- 📌 **로그 수집부터 저장, 분석, 시각화까지** 한 번에 가능한 통합 솔루션이기 때문에 데이터 흐름 파악이 직관적입니다.
- ⚡ **다양한 형식의 데이터 수집과 전처리가 가능**하여 복잡한 원천 데이터를 일관된 포맷으로 가공할 수 있습니다.
- 📊 **Kibana를 통한 실시간 대시보드 시각화**로 인사이트 도출이 용이합니다.
- 🔍 **필터링, 집계, 검색 기능이 강력한 Elasticsearch**를 통해 수많은 데이터 중 원하는 정보를 빠르게 찾을 수 있습니다.
- 🛠 **Docker Compose로 손쉽게 컨테이너화**하여, 테스트 환경 구축 및 배포가 간편합니다.




<br>

## 🔍 참고 사례  

### 📌 디지털 전환 기반 사례  
**"디지털에 힘 싣는 우리카드, 서비스 고도화 '잰걸음'"**  
[👉 기사 바로가기](https://www.ibtomato.com/mobile/mView.aspx?no=11933&utm_source=chatgpt.com)

✅ 우리카드는 **디지털 채널 강화와 맞춤형 마케팅 전략**에 주력하고 있으며,  
**"우리WON카드 앱"** 중심의 **비대면 고객 접점 확대**를 추진 중입니다.  <br>
→ 따라서 **카드 이용 고객의 디지털 채널 유입과 실사용률을 높이는 것**이 핵심 과제입니다. <br>
→ 단순 가입을 넘어, **디지털 채널 ‘실사용’까지 유도하는 전략적 접근이 필요**하고 생각했습니다.

<br>

### 📌 마케팅 효과 중심 사례  
**"시중은행, 올해 광고선전비 줄였다...신한은행만 증가"**  
[👉 기사 바로가기](https://www.ibtomato.com/mobile/mView.aspx?no=11933&utm_source=chatgpt.com)

✅ 카드사와 은행권은 **마케팅 비용의 효율성**을 더욱 중요하게 평가하고 있으며,  <br>
특히 **타겟 고객층에게 정확한 채널을 통해 효과적인 메시지를 전달하는 것**이 중요해지고 있습니다.  <br>
→ 이에 따라 **고객의 채널 이용 행태를 기반으로 어떤 방식의 마케팅이 효과적인지 분석** 하고자 했습니다.

<br>

## 💡 목적 

두 사례를 바탕으로 **ELK Stack**을 활용하여
**디지털 채널 유입과 실사용 간의 간극을 해소하고**,  <br>
**고객 특성에 따라 최적화된 채널 및 메시지를 도출**하여 <br>
**보다 효율적이고 타겟 중심적인 마케팅 전략 수립을 위한 데이터 인사이트**를 도출하는 것이 목표입니다.


<br>

---

# 🛠️ 테스트 환경
- **환경세팅**: Elasticsearch 7.11.2 / Kibana 7.11.2 / logstash 7.11.2 (향후 사용 예정)
- **운영체제**: Windows 11 / ubuntu 24.04

<details>
  <summary>ubuntu docker 설정</summary>
  <div markdown="1">
  
## 📁 프로젝트 디렉토리 구조

```
ElkStack/
│
├── docker-compose.yml
│
├── logstash/
│   ├── config/
│   │   └── logstash.yml
│   └── pipeline/
│       └── logstash.conf
│
├── filebeat/
│   └── filebeat.yml
```

---

## 📦 컨테이너 구성

| 서비스       | 이미지                                           | 포트 매핑              |
|--------------|--------------------------------------------------|-------------------------|
| Elasticsearch | `docker.elastic.co/elasticsearch/elasticsearch:7.11.2` | 9200, 9300              |
| Logstash     | `docker.elastic.co/logstash/logstash:7.11.2`     | 5044, 9600              |
| Kibana       | `docker.elastic.co/kibana/kibana:7.11.2`         | 5601                    |
| Filebeat     | `docker.elastic.co/beats/filebeat:7.11.2`        | -                       |

---

## 📄 docker-compose.yml

```yaml
version: '3.7'

services:
  elasticsearch:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.11.2
    container_name: elasticsearch
    environment:
      - discovery.type=single-node
      - xpack.security.enabled=false
      - ES_JAVA_OPTS=-Xms1g -Xmx1g
    ports:
      - "9200:9200"
    volumes:
      - esdata:/usr/share/elasticsearch/data

  logstash:
    image: docker.elastic.co/logstash/logstash:7.11.2
    container_name: logstash
    volumes:
      - ./logstash/pipeline:/usr/share/logstash/pipeline
      - ./logstash/config:/usr/share/logstash/config
    ports:
      - "5044:5044"
      - "9600:9600"
    depends_on:
      - elasticsearch

  kibana:
    image: docker.elastic.co/kibana/kibana:7.11.2
    container_name: kibana
    environment:
      - ELASTICSEARCH_HOSTS=http://elasticsearch:9200
    ports:
      - "5601:5601"
    depends_on:
      - elasticsearch

  filebeat:
    image: docker.elastic.co/beats/filebeat:7.11.2
    container_name: filebeat
    user: root
    volumes:
      - ./filebeat/filebeat.yml:/usr/share/filebeat/filebeat.yml:ro
      - /var/lib/docker/containers:/var/lib/docker/containers:ro
      - /var/log:/var/log:ro
    depends_on:
      - logstash
      - elasticsearch
    command: ["--strict.perms=false"]

volumes:
  esdata:

```

---

## 🔧 Logstash 설정

**logstash/config/logstash.yml**
```yaml
http.host: "0.0.0.0"
xpack.monitoring.enabled: false
```

**logstash/pipeline/logstash.conf**
```conf
input {
  beats {
    port => 5044
  }
}

output {
  elasticsearch {
    hosts => ["http://elasticsearch:9200"]
    index => "logstash-%{+YYYY.MM.dd}"
  }
}
```

---

## 🔍 Filebeat 설정

**filebeat/filebeat.yml**
```yaml
filebeat.inputs:
  - type: log
    enabled: true
    paths:
      - /var/log/*.log

output.logstash:
  hosts: ["logstash:5044"]
```

> ✅ `filebeat.yml`은 읽기 전용으로 컨테이너에 마운트되며, `logstash` 서비스 이름으로 통신합니다.

---

## 🚀 실행 방법

```bash
# 1. 디렉토리 이동
cd ElkStack

# 2. docker-compose 실행
sudo docker-compose up -d
```

---

## ✅ 동작 확인

```bash
# Elasticsearch
curl http://localhost:9200

# Kibana
http://<서버-IP>:5601

# 로그 확인
sudo docker logs logstash
sudo docker logs filebeat
```

---
## 🔄 NAT 설정을 통한 localhost 접속

ELK Stack 컨테이너들을 외부에서 `localhost`로 접속 가능하도록 하기 위해 **NAT 포트 포워딩**을 설정했습니다. 

### 설정 내용

- `elasticsearch`: 9200 → 9200
- `kibana`: 5601 → 5601
- `logstash`: 5044 → 5044

Docker Compose 파일에서 `ports` 항목을 통해 각 컨테이너의 포트를 호스트의 포트에 바인딩하여 NAT 역할을 하도록 구성했습니다.

```yaml
ports:
  - "5601:5601"  # kibana
  - "9200:9200"  # elasticsearch
  - "5044:5044"  # logstash input
```

이 설정으로 Ubuntu에서 ELK Stack을 실행한 후 브라우저에서 `http://localhost:5601`, `http://localhost:9200` 등으로 접속할 수 있습니다.

또한 다음 명령어를 통해 포트 바인딩 상태를 확인했습니다:

```bash
sudo ss -tuln | grep 5601
```

결과 예시:

```
tcp   LISTEN 0      4096            0.0.0.0:5601       0.0.0.0:*
tcp   LISTEN 0      4096               [::]:5601          [::]:*
```

  </div>
</details>


# 🧩 데이터 셋

### ✅ 인덱스: `cards`
**우리 FISA**에서 제공한 **우리은행 카드 데이터**를 기반으로 한 `cards` 인덱스 구축하였습니다.

### ✅ 인덱스: `range_test_index`
`cards` 인덱스의 거주지 필드를 기준으로 각 거주지에 해당하는 **위도(`lat`)와 경도(`lon`) 정보를 저장**한 보조 인덱스입니다.  
해당 인덱스는 **Kibana의 Geo Map 시각화**를 가능하게 하기 위해 별도로 생성되었으며, 각 지역명과 이를 매핑한 좌표 정보가 포함되어 있습니다.

> **📌 왜 별도로 생성했는가?**  
> `cards` 인덱스는 추후 **데이터 파이프라인(Logstash, Filebeat 등)** 을 통해 정제 및 확장할 예정입니다.  
> 하지만 현재 단계에서는 실험적 시각화 테스트가 주 목적이므로, **원본 데이터의 무결성을 유지**한 상태에서 Geo Map 구성 실습을 진행하고자 `range_test_index`를 별도로 구축하였습니다.

---

## 📊 시각화 구성 (Kibana 대시보드)

| 시각화 종류     | 설명 |
|----------------|------|
| 🥧 **파이 차트** | 고객 등급별 미디어 채널 이용 여부 |
| 📈	**누적 영역 차트** | 미디어 채널 가입 여부별 카테고리 평균값 |
| 📊 **스택 막대 그래프** | 성별에 따른 채널 가입 여부<br/>성별에 따른 채널 이용 여부 |
| 📊 **세로 막대 그래프** | 나이별 미디어 채널 사용 여부 |
| 🍩 **도넛형 차트** | 전체 고객의 미디어 채널 가입 여부<br/>전체 고객의 미디어 채널 이용 여부 |
| 🥧 **원형 차트** | 	고객 등급별 미디어 채널 이용 여부 |
| 🗺 **지도** | *(추후 예정)* |

---
## 📈 주요 분석 결과 상세


### 🔹 1. 전체 고객의 미디어 채널 가입 여부

<img width="490" height="470" alt="Image" src="https://github.com/user-attachments/assets/e1e96ca8-10de-4372-90ad-5da5c9ebb29d" />

#### ✅ 데이터 요약
- 전체 고객 중 **65.05%** 가 디지털(미디어) 채널에 가입하였습니다.
- **34.95%** 는 비가입 상태로, 여전히 오프라인 중심의 고객군이 존재합니다.

#### 🔍 분석 해석

- 디지털 채널에 이미 가입한 **65.05%의 고객**은 디지털에 대한 친숙도와 수용도가 높은 집단으로,  
  **디지털 기반의 맞춤형 마케팅 전략** (예: 푸시 알림, 이메일, 모바일 쿠폰 발송 등) 대상으로 활용 가능하다고 판단됩니다.

- 디지털 채널을 통해 고객 여정 전반(인식 → 관심 → 구매 → 충성)에 대한 **트래킹 및 데이터 기반 캠페인** 실행이 용이합니다.

- 반면, **34.95%의 비가입 고객**은 아직 디지털 접점이 약한 집단으로,  
  **오프라인 중심 커뮤니케이션** 또는 **온·오프라인 연계 전략**이 필요하다는 점을 알 수 있습니다.

---

### 🔹 2. 미디어 채널 가입 후 미디어 채널 사용 여부

<img width="610" height="470" alt="Image" src="https://github.com/user-attachments/assets/0b65fe60-9e60-4681-9987-d90929fc6036" />

#### ✅ 데이터 요약
- 디지털(미디어) 채널에 가입한 고객 중 **63.06%가 실제로는 이용하지 않고 있습니다.**
- 실사용 고객 비율은 가입 고객 대비 **26.12% 낮은 수준**입니다.
- 가입만 하고 이탈하거나 정착하지 못하는 **비활성 사용자 비율이 높은 상태**입니다.

#### 🔍 분석 해석

- 현재 디지털 채널 가입 고객 중 과반 이상이 **실제로 채널을 활용하지 않고 있으므로**,  
  이는 단순 가입으로는 고객 정착이 어렵고, **'활성화' 전략이 매우 중요함을 의미합니다.**

- 디지털 채널에서 고객 정착률이 낮다는 것은 초기 온보딩 또는 고객 경험(UX/UI, 콘텐츠 유용성 등)에 문제가 있을 가능성이 있으며,  
  → 첫 1~2회 사용 과정에서 **고객 이탈이 발생하고 있음을 의미합니다.**  
  이 이탈을 막을 수 있는 방안을 모색해야 합니다.

---

### 🔹 3. 성별에 따른 채널 가입 여부

- 성별 코드 기준: 1 = 남성 / 2 = 여성

<img width="725" height="477" alt="Image" src="https://github.com/user-attachments/assets/c1548319-2037-4b85-9fd4-b223c61b5b19" />

#### ✅ 데이터 요약
- 여성 고객의 디지털 채널 가입률이 남성 대비 상대적으로 높게 나타났습니다.
- 미디어 채널 이용자 다수가 **여성 고객 중심**으로 확인됩니다.

#### 🔍 분석 해석

- **여성 고객군의 디지털 채널 수용도와 참여도가 높아,**  
  디지털 콘텐츠 소비, 이벤트 반응, 커뮤니케이션 참여 등에서 **높은 잠재력이 있습니다.**

- 따라서 디지털 마케팅에서 여성 중심의 **타겟팅이 매우 효과적일 수 있습니다.**  
  예를 들어,  
  - 여성 맞춤형 콘텐츠 및 혜택 제공 (라이프스타일, 쇼핑, 재테크 등)  
  - SNS 및 커뮤니티 기반 마케팅 강화  
  - 연령대별 여성 고객 세분화 → MZ세대와 중장년 여성 대상 각기 다른 메시지 설계

- 반면, 남성 고객군은 상대적으로 **관심도나 진입률이 낮을 가능성이 있으므로,**  
  남성을 위한 특화 서비스나 채널 재설계도 함께 고려할 필요가 있습니다.

---

### 🔹 4. 회원등급별 채널 이용 여부

<img width="984" height="477" alt="image" src="https://github.com/user-attachments/assets/3019cee8-37bf-4508-b603-2f6e23bb5e2d" />

#### ✅ 데이터 요약
- 고객 등급이 낮을수록 디지털 채널 이용률이 낮게 나타났습니다.
- **로열 고객(상위 등급)** 은 디지털 채널을 **적극적으로 활용**하는 경향이 있습니다.
- 저등급 고객은 디지털 채널 **이용률 및 유입량이 현저히 낮은 상태입니다.**

#### 🔍 분석 해석

- **로열 고객층의 높은 채널 활용도는 디지털 접점이 고객 충성도와 밀접한 상관관계를 갖고 있음을 시사합니다.**  
  → 디지털 채널은 **고객과의 관계 강화 및 브랜드 로열티 유지에 매우 효과적인 수단입니다.**

- 반면, 등급이 낮은 고객은 **채널 인지 부족, 관심 저하, 디지털 진입 장벽** 등으로 인해 유입률이 낮은 상태입니다.  
  → 마케팅 전략상 이들에 대한 **진입 유도와 참여 활성화 전략이 시급합니다.**

- **등급별 맞춤 전략 방향은 다음과 같습니다:**  
  - 🔝 **로열 고객군**: VIP 전용 콘텐츠, 디지털 채널 내 전용 서비스, 조기 접근권 제공 등으로 **로열티 강화**  
  - 🟡 **중/하위 고객군**: 디지털 채널 첫 이용 유도형 리워드, '등급 향상 챌린지', 개인화 콘텐츠 제공 등으로 **유입 및 참여 확대**

- 등급과 디지털 채널 이용 간의 연결고리를 활용한 **CRM(고객 관계 관리) 기반 마케팅 자동화**가 필요합니다.

---

### 🔹 5. 나이대별 디지털 채널 사용 여부

<img width="924" height="433" alt="Image" src="https://github.com/user-attachments/assets/c3aeb303-735d-4197-97a0-7e6f49cc7ea3" />

#### ✅ 데이터 요약
- **33~45세 연령층**에서 디지털 채널 사용률이 가장 높았습니다.
- **45~50세 연령층**에서 사용률이 가장 낮게 나타났습니다.
- 연령대에 따른 디지털 채널 수용 격차가 뚜렷하게 확인됩니다.

#### 🔍 분석 해석

- **33~45세는 디지털 친숙도가 높고, 정보 탐색 및 이용에 적극적인 연령대입니다.**  
  → 디지털 기반 핵심 마케팅 타겟으로 활용 가능하며,  
  퍼스널라이징, 자동화 캠페인, 신규 서비스 베타 테스트 참여 대상자로 적합합니다.

- **45세 이상 연령층은 디지털 채널 접근성, 인터페이스 이해도, 사용 동기 부족 등으로 인해 이용률이 낮은 편입니다.**  
  → 단순 가입 유도보다는 **UX 최적화와 교육형 캠페인** 중심 전략이 필요합니다.

- **연령대 기반 마케팅 전략 방향은 다음과 같습니다:**  
  - 👥 **주 이용층(33~45세)**: 고도화된 서비스 제공, 개인화 콘텐츠, 이벤트 참여 확대 유도  
  - 🧓 **저이용층(45~50세)**: 쉬운 UI, 튜토리얼 콘텐츠 제공, 오프라인과 연계한 디지털 체험 유도  
    (예: 지점 방문 고객 대상 앱 체험 이벤트, 1:1 디지털 체험 도우미)

- 연령에 따라 디지털 채널의 **접근성과 기대 효용이 다르므로,**  
  **마이크로 타겟팅 전략과 연령 기반 UX/UI 분기 설계가 필수적입니다.**

---

### 🔹 6. 소비 카테고리별 디지털 채널 평균값

<img width="927" height="436" alt="image" src="https://github.com/user-attachments/assets/d6b13273-7ca9-4065-99ff-fb02b0444a89" />

#### ✅ 데이터 요약
- `용역/수리/건축자재` 카테고리에서 **디지털 채널 이용 고객의 구매율이 가장 높게 나타났습니다.**
- 반면, `가전/가구/주방용품`은 **디지털 채널 이용 유무와 관계없이 구매율이 비슷한 수준이었습니다.**

#### 🔍 분석 해석 (마케팅 전략 관점)

- **서비스형 소비군**(예: 수리, 보험, 요식업 등)은 디지털 채널을 통해 정보 탐색 → 비교 → 구매로 이어지는 흐름이 강합니다.  
  → 디지털 채널에서의 **정보 신뢰도, 접근 용이성, 후속 프로세스(예약, 문의)** 등이 구매로 직접 연결됩니다.

- 반면, **고관여·계획 구매형 품목**(예: 가전/가구 등)은 오프라인 매장 방문, 가격비교, 실제 체험 요소가 여전히 중요합니다.  
  → 디지털 채널의 영향력은 탐색 단계에 머무르거나, 결정 요소로 작용하지 않는 경우가 많습니다.

- **마케팅 전략 방향성은 다음과 같습니다:**  
  - 📱 **디지털 채널 영향력이 큰 카테고리**:  
    - 리뷰 기반 콘텐츠 강화  
    - 비교/추천/예약 기능 강화  
    - 실시간 상담 및 바로 결제 연동  
  - 🛋️ **디지털 영향이 낮은 카테고리**:  
    - 오프라인 연계 콘텐츠 제작 (예: 전시장 미리보기)  
    - 매장 방문 유도 쿠폰, 실물 체험 기반 캠페인 연계  
    - 제품 시뮬레이션(AR/VR 등)을 통해 채널 효용 강화

- **카테고리별 디지털 채널 활용 효율이 다르므로, 각 산업군에 맞는 맞춤 디지털 전략 설계가 중요합니다.**

### 📌 결론  
디지털 채널은 단순 가입률보다 **실사용률과 고객 맞춤 반응이 성공의 관건**이며,  
**고객 특성과 소비 패턴을 고려한 세분화된 마케팅 전략과 옴니채널 경험 제공**이 디지털 전환과 장기 고객 충성도 확보를 이끄는 핵심입니다.
<br/>

# 🚀 트러블 슈팅

## 🚩  나이대별 디지털 채널 사용 여부 분석 시 오류 발생
  나이대별로 미디어 사용 여부를 시각화하려 했으나,  
  Horizontal axis에 나이, Vertical axis에 사용 여부를 직접 적용했을 때  
  **모든 값이 동일하게 출력되어 분석 불가능**한 상황 발생했습니다.

- **해결 방법**  
  - `Horizontal axis`: 나이 
  - `Vertical axis`: `Count` 
  - `Break down by`: 미디어 사용 여부
  이를 통해 **나이대별 디지털 채널 사용 분포를 정확하게 시각화**할 수 있었습니다. <br>
 ✅ *문제 해결 완료*

## 🚩 Kibana 의 MAP 시각화 사용시 이슈

- MAP의 방식을 이용할려고, `위도`, `경도` 가상 필드로 만들었지만 `geo_point` 타입으로 저장되지 않은 형태라 MAP의 방식을 이용 할 수 없었습니다.
- **해결 방법**  
  - **미디어를 이용 중인 고객의 데이터값**을 거주지 정보에 해당하는 위치의 위도,경도를 구하여 python을 이용해 `geo_point`타입으로 **range_test_index** 인덱스에 담아 해당 인덱스를 패턴화 하여 MAP 생성시 사용하여 해결했습니다. <br>
  ✅ *문제 해결 완료*


## 🚩 logstash 환경 설정 시 이슈
- `logstash.yml: is a directory`: 설정 경로가 잘못되어 생기는 에러로, `logstash/config/logstash.yml` 파일이 실제로 **디렉토리**일 경우 삭제 후 파일로 재생성 하지 않았을때 이슈가 발생했습니다.

- **해결 방법**
  포트 접속을 확인 한 후 파일을 재생성 하여 이슈를 확인 하였습니다.
  
  - `ss -tuln | grep 5601` → 포트 열림 확인
  - `ufw status` → 방화벽 설정 확인
  - 클라우드 서버라면 **보안 그룹에서 5601, 9200 포트 오픈 필요**
    
  ```bash
  sudo rm -r ./logstash/config/logstash.yml
  nano ./logstash/config/logstash.yml
  ```
  ✅ *문제 해결 완료*


# 🌟 향후 계획
여러 환경에서도 시도해보고자 향후 계획은 아래와 같습니다.

- **window** 환경에서 파이프라인(filebeat, logstash)를 이용하여 필요한 데이터만 뽑아 만들어 볼 예정입니다.
- **Ubuntu 24.04** 환경에서도 **Docker Compose**를 활용하여 파이프라인(filebeat, logstash)까지 해 볼 예정입니다.
- 지도 시각화는 완전히 구현하지 못했지만, 향후 **Map기능을 활용**하여 **지역 기반 시각적 인사이트를 강화**할 것입니다.
---
