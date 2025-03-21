# Chapter14. 댓글 엔티티와 리파지터리 만들기

## 댓글과 게시글의 관계  
게시판을 보면 하나의 게시글에 수많은 댓글이 달립니다. 이러한 관계를 one-to-many, 즉 **일대다(1:n)관계**라고 한다.  
거꾸로 댓글 입장에서 보면 여러 댓글이 하나의 게시글에 달리므로 many-to-one, 즉 **다대일(n:1)관계**입니다.  

article 테이블과  comment 테이블이 id를 기준으로 관계를 맺고 있습니다. 두 테이블 모두 자신을 대표하는 id가 있는데, id와 같이 자신을 대표하는 속성을 **대표키(기본키)** 라고 한다.  
기본키는 동일 테이블 내에서 중복된 값이 없어야 한다.  
commnet 테이블에는 연관 대상을 가리키는 article_id가 하나 더 있다. article_id와 같이 연관 대상을 가리키는 속성을 **외래키**라 한다.

CommentRepository는 CrudRepository 대신 JpaRepository를 상속받게한다.  
JpaRepository는 ListCrudRepository와 ListPagingAndSortingRepository를 상속받은 인터페이스로 CRUD 기능뿐만 아니라 엔티티를 페이지 단위로 조회 및 정렬하는 기능과 JPA에 특화된 여러 기능 등을 제공한다.  

## 댓글 엔티티 만들기
1.Comment클래스는 엔티티로 사용하므로 @Entity 어노테이션을 붙인다 그리고 클래스에서 사용할 다른 기능도 미리 예상해 @Getter,@ToString,@AllArgsConstructor,@NoArgsConstructor 어노테이션도 추가를 한다.   
2.Comment엔티티는 id(대표키),article(댓글의 부모 게시글),nickname(댓글을 단 사람),body(댓글 본문)로 구성됩니다.   
3.id 필드에 @Id를 붙여 이 필드가 대표키임을 선언한다. 그리고 @GeneratedValue를 붙여 대표키를 자동으로 1씩 증가시킨다. strategy=GerationType.IDENTITY를 추가해 데이터를 생성할 때 마다 DB가 알아서 id 값을 1씩 증사키도록 한다.  
4.article 필드에 @ManyToOne 어노테이션을 붙여 Comment 엔티티와 이 필드가 가르키는 Article 엔티티를 **다대일 관계**로 설정한다.  
5.외래키 매핑은 @JoinColumn 어노테이션을 사용하며 name 속성으로 매핑할 외래키 이름을 지정한다.  
6.나머지 nickname,body 필드에는 @Column 어노테이션을 붙여 Comment 엔티티로 만들어질 테이블의 속성으로 설정한다.  

## 더미 데이터 추가하기
data.sql파일에서 추가한다.  

# 댓글 리파지터리 만들기
형식 - JpaRepository<대상_엔티티, 대표키_값의_타입>  
public interface CommentRepository extends JpaRepository<Comment, Long> {}

## 네이티브 쿼리 메서드
그동안 쿼리는 .sql 문서로 작성하거나 DB 콘솔에서 직접 작성하고 실행했지만 쿼리를 메서드로 작성할 수 있게 하는걸 **네이티브 쿼리 메서드**라고 합니다.
**네이티브 쿼리 메서드**를 만드는 방법은 두 가지인데 **@Query** 어노테이션을 이용하거나 **orm.xml파일**을 이용하는 방법이 있습니다.

## @Query
**SQL**과 유사한 **JPQL**이라는 객제 지향 쿼리 언어를 통해 쿼리를 처리할 수 있도록 지원하는 어노테이션입니다. 기존의 SQL 문을 그대로 쿼리 언어러 사용하고 싶다면 nativeQuery 속성을 true로 설정하면 된다.

## 네이티브 쿼리 XML
메서드에서 수행할 쿼리를 XML로 작성한 것을 말한다. 네이티브 쿼리 XML의 기본 경로와 파일 이름은 META-INF > orm.xml입니다. 이 경로와 이름으로 파일을 만들면 XML이 자동으로 인식된다.

## orm.xml 코드 작성 방법
orm.xml 파일이 생성되면 먼저 엔티티 매핑을 위한 XML 기본 코드를 작성 후 <entity-mappings> 태그 안에 <named-native-query>와<query> 태그를 이용해 쿼리를 입력한다.

## @DataJpaTest
JPA와 연동한 테스트를 연동하는 어노테이션이다. 이를 통해 리파지터리와 엔티티 등의 객체를 테스트 코드에서 사용할 수 있다.

## DisplayName
테스트 이름을 붙일 때 사용하고 기본적으로 테스트 이름은 메서드 이름을 따라간다.  
메서드 이름은 그대로 둔 채 테스트 이름을 바꾸고 싶을 때 이 어노테이션을 사용한다.




