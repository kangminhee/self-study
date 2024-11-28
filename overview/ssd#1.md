개인 공부용으로 작성되었습니다.   

# what is FW?

(in storage device's view)   
- host requirement: pc, server, mobile, ...   
- host가 data를 원할 때 읽거나 쓸 수 있게 하는 storage   
- nand를 이용해 고성능 저전력 storage인 SSD를 만들어냄


about SSD:
- NAND는 고집적 비휘발성 메모리 반도체
- 다루기 까다로우며 그 특성은 세대, 회사 별로 다름
- 일정 수준의 r/w speed, 쉬운 사용성 요구
- 통신 방식 (새로운 통신 프로토콜 재정되기도 함)


FW as SSD component
- NAND, interface and logic SoC chip 하나에 구현 가능

- 변경 가능한 다양한 요구 사항을 만족시키기 위해   
- 변경 가능한 다양한 요구 사항들을 만족 시키기 위해 SoC에 software가 구동되는 processor을 넣어 SW가 변경

- FW 사용 디자인 개발비용/유지보수비용/재사용성 측면에서 제조사에게 많은 이득을 안김

SSD architecture:
- RAM buffer, host, host interface logic, SSD controller, flash memory packages

SSD controller:   
- processor, flash controller, buffer manager

- processor에서 FW가 구동됨
    * 변경 가능성이 낮은 것들은 하드웨어로 설계됨
    * 기존과 유사한 사용성을 제공하기 위해 FW


FW architecture:

- HIL(host interface layer)
- FTL(flash translation layer)
- FIL(flash interface layer)