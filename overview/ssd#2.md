개인 공부용으로 작성되었습니다.   

# what is HIL FW

- host interface와 관련된 기술 구현
- host와 가장 가까운 HIL FW
- host의 명령을 해석하고 처리함
- 저장 장치의 성능 파워 온도 관리

Host Interface 살펴보기 [wiki](https://ko.wikipedia.org/wiki/SATA_익스프레스)
- SATA(serial ATA): 직렬 ATA; 데이터 전송을 주요 목적으로 만든 컴퓨터 버스의 한 가지
- AHCI: SATA -> NVMe 과도기
- NVMe: PCI Express Interface를 통해 버스에 부착된 비휘발성 기억 매체 접근을 위한 논리 장치 Interface 사양이다.
* NVM(non volatile memory) [nvmexpress](https://nvmexpress.org)   
* 성능비교 [link](https://www.cgdirector.com/benefit-m2-nvme-ssd)

### HIL FW: command 처리
- host command를 device로 전달
- submission queue / completion queue


### HIL FW: 성능
- prefetch

### HIL FW: 파워/온도 관리
- NVMe 파워 관리 solution: host가 파워 관리/device가 파워를 관리
- 온도: 성능 제한, 클럭 주파수 낮춤
