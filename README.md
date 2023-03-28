# GGO-BOOK

>독서일정관리 서비스(리더스 벤치마킹)
><br> 프로젝트 개요 -> <a href="https://github.com/sungjiRyu/Prj02/files/11084185/2.pdf" target="_blank"><img src="https://img.shields.io/badge/PPT-F46D01?style=flat&logo=PPT&logoColor=white" /></a>



<br>

## 목차
1. [제작 기간 & 제작 인원](#1-제작-기간--제작-인원)
2. [담당 파트](#2-담당-파트)
3. [사용 기술](#3-사용-기술)
4. [ERD 설계](#4-erd-설계)
5. [주요 코드](#5-주요-코드)


<br><br><br>

## 1. 제작 기간 & 제작 인원
- 2022/02/08 ~ 2023/03/03
- 참여인원 6명(프론트 2명, 백엔드 4명)

<br><br><br>

## 2. 담당 파트
게시판 CRUD 작업
- 게시글 CRUD
- 게시글 조회(검색어로 검색) 
- 댓글 CRUD


<br><br><br>

## 3. 사용 기술
>**Back-end**<br>
<div align=center>
  <img src="https://img.shields.io/badge/Java-007396?style=flat&logo=Conda-Forge&logoColor=white" />
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=MySQL&logoColor=white"/>
  <img src="https://img.shields.io/badge/Spring Boot-6DB33F?style=flat&logo=Spring Boot&logoColor=white"/>
  <img src="https://img.shields.io/badge/Gradle-02303A?style=flat&logo=Gradle&logoColor=white"/>
  <img src="https://img.shields.io/badge/JPA-59666C?style=flat&logo=JPA&logoColor=white"/>
  <img src="https://img.shields.io/badge/Tomcat-F8DC75?style=flat&logo=Apache Tomcat&logoColor=white"/>
  <img src="https://img.shields.io/badge/Redis-DC382D?style=flat&logo=Apache Redis&logoColor=white"/>
   <img src="https://img.shields.io/badge/Swagger-85EA2D?style=flat&logo=Apache Swagger&logoColor=white"/>
</div>



>**형상관리**<br>
<div align=center>
<img src="https://img.shields.io/badge/GitHub-181717?style=for-the-flat&logo=GitHub&logoColor=white">
<img src="https://img.shields.io/badge/Git-F05032?style=for-the-flat&logo=Git&logoColor=white">
</div>

<br><br><br>

## 4. ERD 설계
![화면 캡처 2023-03-28 100617](https://user-images.githubusercontent.com/116089824/228100439-db54ea0f-4098-4809-839d-ea06d5e84248.jpg)



<br><br><br>

## 5. 주요 코드

<br>

### 5.1 게시글 검색
```
public interface ArticleInfoRepository extends JpaRepository<ArticleInfoEntity, Long>{
    //게시글 리스트 조회
    @Query("SELECT a FROM ArticleInfoEntity a WHERE a.aiStatus = 1 AND a.aiPurpose = 1 AND a.aiPublic = 1")
    public Page<GetSearchArticleVO> findAllArtilce(Pageable pageable);
    // 제목으로 게시글 검색
    @Query("SELECT a FROM ArticleInfoEntity a WHERE a.aiStatus = 1 AND a.aiPurpose = 1 AND a.aiPublic = 1 AND a.aiTitle LIKE %:keyword%")
    public Page<GetSearchArticleVO> findByAiTitleContains(@Param("keyword") String keyword, Pageable pageable);
    // 내용으로 게시글 검색
    @Query("SELECT a FROM ArticleInfoEntity a WHERE a.aiStatus = 1 AND a.aiPurpose = 1 AND a.aiPublic = 1 AND a.aiContent LIKE %:keyword%")
    public Page<GetSearchArticleVO> findByAiContentContains(@Param("keyword") String keyword, Pageable pageable);
```

<br>

> 검색어(keyword)를 통해 게시글을 검색할 수 있습니다.

<br><br><br>



<br>
