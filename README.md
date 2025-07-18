# 📊 ELK 미디어 채널 이용 분석
우리 FISA 아카데미에서 제공해준 우리은행 카드정보를 활용하여 ELK을 통해 미디어 채널 이용을 분석한 프로젝트입니다.

# 👥팀소개
<div align="center">
  
|신준수|문민경|최소영|장송하|
|:---:|:---:|:---:|:---:|
|[shinjunsuuu](https://github.com/shinjunsuuu)|[Minkyoungg0](https://github.com/Minkyoungg0)|[](https)|[jangongha](https://github.com/songhajang)|
|<img width="200" height="250" alt="Image" src="https://github.com/shinjunsuuu.png" />|<img width="200" height="250" alt="Image" src="https://github.com/user-attachments/assets/94f643a0-b74f-42ec-8eb4-e00ffcae4ef1" />|<img width="200" height="250" alt="Image" src="" />|<img width="200" height="250" alt="Image" src="https://github.com/user-attachments/assets/36f811b5-e8e9-43f4-b833-b4b9dae40e82" />|
  
</div>

### ❓ELK 란
**ELK Stack**은 로그 및 데이터 분석, 시각화를 위한 오픈소스 기반 통합 플랫폼입니다.  
**Elasticsearch**, **Logstash**, **Kibana**의 머리글자를 따서 ELK라 부르며,  로그 분석, 보안 모니터링, 트랜잭션 추적, 사용자 행동 분석 등에 활용됩니다.

**각 요소별로 하는 역할**

- 🔎 **Elasticsearch**:  
  실시간으로 데이터를 저장하고 검색할 수 있는 분산형 검색 및 분석 엔진입니다.

- 🛠️ **Logstash**:  
  다양한 소스로부터 데이터를 수집하고 변환하여 Elasticsearch로 전달하는 데이터 파이프라인 도구입니다.

- 📊 **Kibana**:  
  Elasticsearch에 저장된 데이터를 시각화하고, 대시보드를 구성할 수 있는 사용자 인터페이스 도구입니다.


<br>

# 🧭 프로젝트 목적

본 프로젝트는 **ELK Stack**을 활용하여 `cards` 인덱스의 데이터를 기반으로  
**미디어 채널 가입 여부와 사용 여부에 따라**  
- 거주 지역  
- 나이  
- 성별  
- 회원 등급  
- 소비 카테고리  

등 다양한 고객 특성을 분석하였습니다.  
이를 통해 **주요 미디어 채널을 이용하는 고객의 특성과 패턴을 파악**하고,  
마케팅 및 채널 전략 수립에 필요한 인사이트를 도출하는 것을 목표로 하였습니다.

<br>

## ✅ 미디어 채널 분석을 선택한 이유

- 🎯 **연령대별 타겟 마케팅 전략 수립**을 위한 기반 데이터 확보  
- 🧭 **회원 등급 및 지역 기반 미디어 채널 운영 전략 강화**  
- 🚀 디지털 미이용 고객 발굴 및 **디지털 전환 촉진 방안 마련**

---

# 🛠️ 테스트 환경
- **환경세팅**: Elasticsearch 7.11.2 / Kibana 7.11.2 / logstash 7.11.2 (향후 사용 예정)
- **운영체제**: Windows 10
---

# 🧩 데이터 셋

### ✅ 인덱스: `cards`
**우리 FISA 아카데미**에서 제공한 **우리은행 카드 데이터**를 기반으로 한 `cards` 인덱스 구축하였습니다.

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

- 전체 고객 중 **65.05%** 가 디지털(미디어) 채널에 가입한 상태입니다.
- 디지털 가입률이 과반 이상이며, **디지털 환경에 익숙한 고객이 다수** 존재합니다.
- 그러나 **34.95%는 비가입 상태**로, 여전히 오프라인 중심 고객군 적지 않은 비율을 포함하고 있다는걸 알 수 있습니다.

---

### 🔹 2. 성별에 따른 채널 가입 여부

- 성별 코드 기준:  1 = 남성  | 2 = 여성

<img width="725" height="477" alt="Image" src="https://github.com/user-attachments/assets/c1548319-2037-4b85-9fd4-b223c61b5b19" />

- 여성 고객의 디지털 채널 가입률이 상대적으로 **높게 나타납니다**
- 마케팅 시 성별 특성에 따른 접근 전략 필요하다는걸 알 수 있습니다.
- 미디어 채널의 이용자가 대다수 여성인것을 토대로 이벤트 광고 및 타겟층을 여성으로 잡을 수 있다는것을 알 수 있습니다.

---

### 🔹 3. 전체 고객의 미디어 채널 사용 여부


<img width="610" height="470" alt="Image" src="https://github.com/user-attachments/assets/0b65fe60-9e60-4681-9987-d90929fc6036" />


- 전체 고객 중 **63.06%** 가 디지털(미디어) 채널을 이용하지 않는 상태입니다.
- 디지털 가입률이 반대로 , **디지털 이용하는 고객은 이용하는 고객보다 26.12%** 적습니다.
- 가입 이후 **실질적 사용 유도**를 위한 전략 필요하다는걸 알 수 있습니다.


---

### 🔹 4. 성별에 따른 채널 사용 여부
<img width="600" height="300" alt="Image" src="https://github.com/user-attachments/assets/b5c893f8-e601-4574-abc9-49d5b5ec2ea5" />
<img width="600" height="300" alt="Image" src="https://github.com/user-attachments/assets/b917872f-3f32-44c7-86cd-a8e33690ad69" />
<!--<img width="803" height="503" alt="Image" src="https://github.com/user-attachments/assets/93758533-0548-4bce-bec8-bbfb57d33f87" /> -->

- **여성 고객의 채널 사용률이 남성 고객과 0.66% 차이로 미미합니다.** 

---

### 🔹 5. 회원등급별 채널 이용 여부

<img width="561" height="509" alt="Image" src="https://github.com/user-attachments/assets/c2bc206f-6b30-4d49-9dbe-cada141032ad" />

- 높은 등급일수록 디지털 채널 사용률이 높습니다.
- **로열 고객군이 디지털 채널을 적극적으로 이용**하는 경향으로 확인이 가능햇으며,
- 등급이 낮은 고객의 채널 유입 전략 필요하다는걸 확인 할 수 있습니다.

---

### 🔹 6. 나이대별 디지털 채널 사용 여부

<img width="924" height="433" alt="Image" src="https://github.com/user-attachments/assets/c3aeb303-735d-4197-97a0-7e6f49cc7ea3" />

- **33~45대에서 가장 높은 사용률**을 보입니다.
- 또한 **45~50대 에서 가장 낮은 사용률**을 보입니다.
- 연령대 기반으로 UX 개선 또는 비고객층 미디어 채널 캠페인이 필요한것으로 확인 할 수 있습니다.

---

### 🔹 7. 소비 카테고리별 디지털 채널 평균값

<img width="927" height="436" alt="image" src="https://github.com/user-attachments/assets/d6b13273-7ca9-4065-99ff-fb02b0444a89" />

- `용역/수리/건축자재`, `요식업`, `여행/레져/문화` , `사무통신/서적/학원`, `보험/병원`, `가전/가구/주방용품` 등 일상 소비 중심 카테고리에서 디지털 채널 이용한 고객의 구매율이 `용역/수리/건축자재` 가장 높았습니다.
- 반면, `가전/가구/주방용품`은 미디어 채널을 이용하지 않는 고객과 이용한 고객이 동등한 구매율을 보입니다.
- **소비 유형에 따라 디지털 채널의 효용 인식을 강화하여** 고객의 구매율 유도를 노리는것이 필요합니다.

---

## 🔍 테스트 결과에 대한 고찰

- 단순 사용률 수치 외에도, **비이용 고객군의 명확한 특성 도출**이 가능했음
- ELK 대시보드를 통해 실시간으로 데이터 흐름과 분포 파악이 쉬웠고,  
  특히 **Kibana의 시각화 기능**을 통해 분석 인사이트 도출이 용이했음
- 향후 유사한 프로젝트에 있어 ELK는 **데이터 기반 마케팅 전략 수립 도구**로 충분히 유효하다고 판단됨

---

## ✅ 결론

- 디지털 채널 이용률은 **연령, 성별, 등급, 지역, 소비유형**에 따라 유의미한 차이를 보였음
- 마케팅 및 서비스 전략 수립 시, 이러한 특성을 고려한 **맞춤형 접근 전략이 필요**
- 본 분석 결과는 **디지털 전환률을 높이고, 채널 운영 효율성을 개선**하는 데 실질적인 도움을 줄 수 있음

<br>

# 🚀 트러블 슈팅

## 🚩 Kibana 의 MAP 시각화 사용시 이슈

- MAP의 방식을 이용할려고, `위도`, `경도` 가상 필드로 만들었지만 `geo_point` 타입으로 저장되지 않은 형태라 MAP의 방식을 이용 할 수 없었습니다.
- **해결 방법**  
  - **미디어를 이용 중인 고객의 데이터값**을 거주지 정보에 해당하는 위치의 위도,경도를 구하여 python을 이용해 `geo_point`타입으로 **range_test_index** 인덱스에 담아 해당 인덱스를 패턴화 하여 MAP 생성시 사용하여 해결했습니다. <br>
  ✅ *문제 해결 완료*


# 🌟 향후 계획
- 파이프라인(filebeat, logstash)를 이용하여 필요한 데이터만 뽑아 만들어 볼 예정입니다.
- 현재 환경은 window 로 제작하여 향후엔 Liunx 에서도 구동구현을 해 볼 예정입니다.
- **Ubuntu 24.04** 환경에서 **Docker Compose**를 활용하여 ELK Stack (Elasticsearch, Logstash, Kibana)과 Filebeat를 구성

---

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

## ❗ 트러블 슈팅

- `logstash.yml: is a directory`: 설정 경로가 잘못되어 생기는 에러로, `logstash/config/logstash.yml` 파일이 실제로 **디렉토리**일 경우 삭제 후 파일로 재생성
  ```bash
  sudo rm -r ./logstash/config/logstash.yml
  nano ./logstash/config/logstash.yml
  ```

- 포트 접속 안 될 때:
  - `ss -tuln | grep 5601` → 포트 열림 확인
  - `ufw status` → 방화벽 설정 확인
  - 클라우드 서버라면 **보안 그룹에서 5601, 9200 포트 오픈 필요**

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
