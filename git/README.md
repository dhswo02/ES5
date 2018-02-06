##설정과 초기화
> 전역사용자명/이메일 구성

    git config --global user.name `Your Name` 
    git config --global user.email `Your email address`
    
> 저장소별 사용자명/이메일 구성하기 (해당 저장소 디레터리로 이동 후)

    git config user.name `Your name`
    git config user.email `Your email address`
    
> 설정 정보 조회

    //  전역
    git config --global --list
    
    //  저장소별
    git config --list
    
> Git 출력결과 색상 활성화하기

    git config --global color.ui 'atuo'
    
> 새로운 저장소 초기화 하기
    
    mkdir/path/newDir
    cd/path/newDir
    git init
    
> 저장소 복제하기

    git clone <저장소 url>
    
> 새로운 원격 저장소 추가하기

    git remote add <원격 저장소> <저장소 url>
    
> 새로운 파일을 추가하거나 존재하는 파일 스테이징하고 커밋
    
    git add <파일>    
    git commit -m '<메세지>'
    
> 지역 브랜치 목록 보기

    git branch

> 원격 브랜치 목록 보기

    git branch -r

> 지역과 원격을 포함한 모든 브랜치 목록 보기

    git branch -a
    
> 현재 브랜치에서 새로운 브랜치 생성하기

    git branch <새로운 브랜치>
    
> 다른 브랜치 체크아웃하기

    git checkout <브렌치>
    
> 현재 브랜치에서 새로운 브랜치 생성하고 체크아웃하기

    git checkout -b <새로운 브랜치>
    
> 기존 브랜치를 새로운 브랜치로 덮어쓰기

    git branch -f <기존 브랜치> [<브랜치를 생성할 위치>]
    
> 다른 브랜치를 현재 브랜치로 합치기

    git merge <브랜치>
    
> 커밋하지 않고 합치기

    git merge --no-commit <브랜치>
    
> 선택하여 합치기

    git cherry-pick <커밋명>
    
> 커밋하지 않고 선택하여 합치기

    git cherry-pick -n <커밋명>
    
> 브랜치 삭제하기
    
    //  삭제할 브랜치가 현재 브랜치에 합쳐졌을 경우에만
    git branch -d <삭제할 브랜치>
    
    //  삭제할 브랜치가 현재 브랜치에 합쳐지지 않았어도
    git branch -D <삭제할 브랜치>
   