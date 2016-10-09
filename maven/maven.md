# Study1
## Maven学习

### 1、mvn -v ：查看当前Maven的版本。
### 2、mvn compile：编译项目
### 3、mvn test ：先编译然后执行测试代码
### 4、mvn package：生成target目录，编译、测试代码，生成测试报告，生成jar/war文件
### 5、mvn clean：删除target(编译生成的字节码和测试报告)
### 6、mvn install：将打包生成的Jar文件存放到本地仓库，方便以后其他项目调用，直接在pom.xml中添加依赖即可。
### 7、mvn javadoc:jar生成对应的javadoc
   在Maven项目的根目录即pom.xml文件所在的目录下使用mvn javadoc:jar可以生成当前项目对应的java doc。
### 8、使用mvn dependency:sources下载对应的源码
   在Maven项目的根目录即pom.xml文件所在的目录下使用mvn dependency:sources可以下载对应依赖包的源码。

### 使用Maven来管理项目的目录骨架：
src
		|--------main  主要代码
				|---java
					|----package
		|---------test  测试代码
				  |--java
					 |---package
		|----------resources
pom.xml

## pom.xml中的配置信息
   pom.xml文件是Maven进行工作的主要配置文件。在这个文件中我们可以配置Maven项目的groupId、artifactId和version等Maven项目必须的元素；
   可以配置Maven项目需要使用的远程仓库；可以定义Maven项目打包的形式；可以定义Maven项目的资源依赖关系等等。
   对于一个最简单的pom.xml的定义必须包含modelVersion、groupId、artifactId和version这四个元素，
   当然这其中的元素也是可以从它的父项目中继承的。
   在Maven中，使用groupId、artifactId和version组成groupdId:artifactId:version的形式来唯一确定一个项目
   (maven中任何一个依赖、插件都可以被称为构件。所有构件通过坐标作为其唯一标识。)
   
```xml
    <modelVersion>4.0.0</modelVersion>  <!-- maven版本，此值固定-->

    <!-- 项目 -->
    <groupId>org.gpf.maventest01</groupId><!--项目包名-->
    <artifactId>maventest01</artifactId>  <!-- 模块名，建议使用项目名 -->
    <version>0.0.1SNAPSHOT</version>    <!--版本，此处为快照版本-->

    <!-- 依赖列表 -->
    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.10</version>
            <scope>test</scope><!-- 依赖范围，只能在test -->
            <optional></optional><!-- 依赖是否可选，默认是false -->
            <exclusions><!-- 排除依赖传递传递列表 -->
                <exclusion></exclusion>
            </exclusions>
        </dependency>
    </dependencies>
```


