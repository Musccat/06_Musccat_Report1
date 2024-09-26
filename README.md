<!-- Template for PROJECT REPORT of CapstoneDesign 2024-2H, initially written by khyoo -->
<!-- 본 파일은 2024년도 컴공 졸업프로젝트의 <1차보고서> 작성을 위한 기본 양식입니다. -->
<!-- 아래에 "*"..."*" 표시는 italic체로 출력하기 위해서 사용한 것입니다. -->
<!-- "내용"에 해당하는 부분을 지우고, 여러분 과제의 내용을 작성해 주세요. -->

# Team-Info
| (1) 과제명 | *자신에게 적합한 장학금을 찾는 대학생을 위해 생성형 ai를 이용하여 각 사용자에게 맞는 장학금을 추천하고 이전 수혜자들의 조언을 바탕으로 장학금 수혜 팁을 제공해주는 서비스*
|:---  |---  |
| (2) 팀 번호 / 팀 이름 | *06-머스캣* |
| (3) 팀 구성원 | 채민주 (0000000): 리더, React 프론트엔드 개발, 프로토타입 제작, 프론트엔드 배포환경 세팅 <br> 이서연 (0000000): 팀원, 추천 알고리즘 개발, 수혜팁 추출 기능 개발, Django API 개발<br> 변하영 (0000000) : 팀원, Django API 개발, 프로토타입 제작, 백엔드 배포환경 세팅			 |
| (4) 팀 지도교수 | 심재형 교수님 |
| (5) 팀 멘토 | 이수현 / 개발자 / 네이버 |
| (6) 과제 분류 | *산학과제 * |
| (6) 과제 키워드 | *데이터베이스, 머신러닝, 자연어처리, 추천시스템*  |
| (7) 과제 내용 요약 | *전체 과제 내용을 10줄이내로 설명* |

<br>

# Project-Summary
| 항목 | 내용 |
|:---  |---  |
| (1) 문제 정의 | *본 과제를 통하여 해결/완화하고자하는 문제에 대하여 기술. Target Customer 정의와 해결해야 할 문제점들(pain points)대한 내용 기술*  |
| (2) 기존연구와의 비교 | *유사한 과제/연구/서비스/시스템의 예를 들고, 각각의 장단점을 기술할 것. 특히, 본 과제가 유사과제에 대하여 갖는 장점을 부각할 것* |
| (3) 제안 내용 | *본 프로젝트에서 제시한 문제를 해결하기 위해 새롭제 제안하는 해결책 or 해결책들에 대하여 기술 .* |
| (4) 기대효과 및 의의 | *프로젝트의 결과물을 통하여 얻을 수 있는 기대효과 및 의의에 대하여 기술 .* |
| (5) 주요 기능 리스트 | *(3)에서 제안한 해결책들을 지원or구현하기 위하여 필요한 주요 기능 혹은 기능을을 List-up하고, <br> 각각에 대하여 설명* |

<br>
 
# Project-Design
| 항목             | 내용                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| :------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| (1) 요구사항 정의    | **유저플로우**<br>![[./image/user_flow.png]]<br>**ER다이어그램**<br>![[./image/er_diagram.png]]<br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| (2) 전체 시스템 구성  | ![[./image/system_architecture.png]]<br>1. 프론트엔드<br>React로 개발된 프론트엔드를 Vercel로 배포하고, Axios를 통해 백엔드와 통신합니다. <br>2. 백엔드<br>Nginx, Gunicorn과 Django 애플리케이션을 Docker를 이용해 컨테이너화하여 독립적으로 관리합니다. 그리고 EC2 인스턴스를 이용해 Docker 기반의 백엔드를 배포합니다. <br>3. 데이터베이스<br>Amazon RDS에서 MySQL 데이터베이스를 운영하고 EC2와 RDS 연동을 통해 데이터베이스 접근과 관리를 효율적으로 수행합니다.<br>4. 외부 서비스 연동<br>OpenAI를 이용하여 맞춤형 장학금 추천 및 수혜 팁 추출 기능을 구현하고 PortOne을 이용하여 포인트를 충전하기 위한 결제 시스템을 구축합니다.<br>                                                                                                                                                                                                                                                                                                                                       |
| (3) 진척도 및 검증내역 | **스타트 단계에서 검증한 내용**<br>1. 맞춤형 추천 시스템 기술 검증<br>- 사용자의 프로필(전공, 성적, 경제적 상황, 관심 분야, 대외활동 내역 등)과 관련된 장학금을 추천하는 시스템의 기술 검증을 진행하였습니다. <br>- 여러 방법을 시도한 결과, GPT 4o-mini를 활용하여 지역 조건을 먼저 선별한 후 다른 조건들을 필터링하는 방법이 가장 성능이 우수하여 해당 방법을 최종 선택하였습니다. <br>2. 수혜 팁 추출 기술 검증<br>- 수집한 이전 수혜자들의 합격팁과 면접팁을 바탕으로 중요한 내용을 추출하여 수혜팁을 제공하는 기능의 기술검증을 진행하였습니다. <br>- 임의로 입력한 수혜자들의 합격팁과 면접팁을 바탕으로 중요한 내용을 추출하여 정리할 수 있도록 GPT 프롬프트를 작성하였습니다. <br><br>**현재 진척도 및 근거 내용**<br>1. 프론트엔드<br>- UI/UX 디자인을 바탕으로 개발 진행 중 (현재 약 70% 완료)<br>- 백엔드와 연동 작업 진행 중 (현재 약 40% 완료)<br>- 프론트엔드 서버 배포환경 세팅 완료<br>2. 백엔드<br>- API 명세서와 ER다이어그램을 바탕으로 API 개발 진행 중 (현재 약 60% 완료)<br>- 백엔드 서버 배포환경 세팅 진행 중 (현재 약 70% 완료)<br>3. AI<br>- 스타트 단계에서 진행했던 기술 검증을 바탕으로 맞춤형 추천 시스템과 수혜 팁 추출 기능 구축 완료<br>- 백엔드와의 연동 작업 진행 중(현재 약 60% 완료) |
| (4) 기타         | *기타 사항을 기술*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

<br>