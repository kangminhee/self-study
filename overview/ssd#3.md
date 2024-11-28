개인 공부용으로 작성되었습니다.   

# what if FTL? (ATL)

- map
- read buffer
- write buffer
- garbage collection

### ATL(address translation layer)

#### map
- address translation (from logical address to physical)
- LBA(logical block address; 512B/block) -> LPN(logical page number; 4KB) -> VPN(virtual page nuber; 4KB)
    * LBA / 8 = LPN
    * VPN = | super block ID | page(or WL) No. | bit per cell | die ID | plane | slice
- mapping table
    * uses 4B map data for 4KB user data

#### buffer(cache)
- read buffer
    * cell array -(tR 만큼 시간이 걸림)> page buffer -(D-out; via channel)> read buffer -(interface)> host
- write buffer
    * LBA 단위와 NAND PGM 단위 불일치로 인해 필요
    * host -(gathering, aggregation)> write buffer -(D-in; via channel)> page buffer -(tPROG 만큼 시간이 걸림)> cell array
    * early completion (power loss -> data loss 가능) -> flush command

#### garbage collection
: NAND는 erase 이후 page 단위로 한 번씩만 기록할 수 있음    
기록된 내용을 변경하기 위해서는 새로운 위치에 다시 기록하여야 함
- what GC does: valid 이동, garbage 누적
- garbage collection 원리
    * free block 생산량과 소모량을 일치시킨다.

### VFL

#### bad block
- MBB(manufacturing bad block)
- GBB(grown bad block): end user 실사용 중 발생된 bad block
    * read failure: error bit가 너무 많아서 복구 불가능한 경우
    * program status failure: status read 결과가 실패인 경우
    * erase status failure: erase 동작에 대한 status read 결과가 실패인 경우

#### super block remap
- 모든 die, 모든 plane