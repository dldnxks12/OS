Unix에서는 디스크, 터미널 사운드 카드 등의 Device들을 모두 하나의 file로 취급한다. 

	→ Linux는 Device도 file로 취급하므로, 디바이스 파일을 통해 device 장치에 접근 가능

위와 같은 파일들을 관리하는 시스템을 파일 시스템이라 한다.

이 파일 시스템은 SSD, HDD, USB 등과 같은 물리적인 기억장치 위에 존재한다.

예를 들어, SSD, HDD는 디스크를 파티션(Partition)단위로 쪼개고, 그 위에 파일 시스템을 얹어서 마운트한다.

이렇게 하면 거대한 디렉토리 트리가 생성된다. 

	'mount' 명령어를 이용해서 지금 사용하고 있는 시스템에서 어떤 파일 시스템을 사용하는지 알 수 있다. 


####		다양한 파일 시스템 

			1. ext4 : 현재 Linux에서 가장 많이 쓰이는 파일 시스템

			2. xfs  : 구 SGI 사가 제공한 저널링 파일 시스템

			3. btrfs: Linux 향 파일 시스템

####            가상 파일 시스템 

		위의 파일 시스템 외에도 procfs, tempfs, devfs 등의 파일 시스템이 존재한다.

		이 것들은 ext4와 같이 물리적인 디바이스가 존재하지 않는다.
	
		이런 파일 시스템을 '가상 파일 시스템' 이라한다!

- File

    1. 루트 파일 시스템

        → 시스템 초기화 및 관리에 필요한 내용을 담은 파일

        → 부팅에 필수

    2. 일반 파일

        → 프로그램 파일 , 원시 프로그램, 텍스트 파일 등

    3. 디렉터리 파일

        → 다른 파일과 디렉토리에 관한 정보를 저장하는 논리적인 단위 파일

        → 아이노드라는 Unix 자료구조로 관리

    4. 특수 파일 

        → 디바이스들을 위한 파일 

        → named pipe, symbolic link file, device file 등 

		-> named pipe : 프로세스 간 통신에 사용하는 파일 (FIFO)

        → 디바이스 파일을 통해 장치에 접근, 제어 가능 



#### link - Hard link & Soft link(Symbolic link)

Linux권한은 사용자와 그룹으로 나눌 수 있다.

- 사용자

    → 계정, 비밀번호, UID로 식별

- 그룹

    → GID 로 식별


####  ls -l : file에 대한 메타 정보 확인 Command


1. file type 

2. rwx (read write execute) : 소유자 → 그룹 → 다른 사람 순

    → 권한 변경 : chmod 이용 

    Method 1. 문자열 변경

    → chmod [-R] 새 모드 {file name}+

    → u(user/owner) , g(group) , o(others), a(all)

    → + , - r w x 

    ex) sudo chmod ug+x 1.txt

    Method 2. 8진수 이용 설정

    ex) sudo chmod 777 1.txt

3. link 수 

4. 소유자 → chown 으로 변경

5. 그룹     → chgrp 으로 변경 

6. 크기 (byte)

7. 최종 변경 일자

8. file name
