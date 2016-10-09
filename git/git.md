# Study1
## git学习(Bash)
### 1、git init：初始化仓库
		在需要使用git来管理的项目目录中，使用此命令来初始化仓库。
### 2、git status：查看仓库的状态
### 3、git add：向暂存区中添加文件
	git add .：一次性加入当前目录中的全部文件
	git add –i: 使用互动模式来提交文件
### 4、git	commit：保存仓库的历史纪录
### 5、git diff：查看工作树与暂存区的差别
### 6、git diff HEAD：查看工作树与最新提交的差别
### 7、git log：查看提交日志
   git log --pretty=short：只显示提交信息的第一行
   git log 文件名：只显示指定目录、文件的日志
   git log -p 文件名：显示指定文件的改动，查看提交所带来的影响
### 8、git branch：显示分支览表，将会列出当前所有分支，左侧标有*表示当前所在分支
   git checkout –b 分支名称：创建、切换分支，若分支存在，则直接切换，若分支不存在则创建并切换，
   等同于：
   git branch 分支名称
   git checkout 分支名称
### 9、git merge：合并分支
### 10、git remote add：添加远程仓库
   git remote add 主机名 远程仓库的地址，之后就可以使用主机名来代替远程仓库
   git push -u 主机名 master：将master分支提交的历史记录推送至远程仓库GitHub
   git checkout -b 新的分支名称 主机名/要下载到本地的分支名称：
	将远程仓库的某个分支中的文件下载到本地(本地没有此分支)
   git remote：列出所有远程主机。
   git remote -v：列出所有主机的名称和对应的网址
   git remote show 主机名：可以查看该主机的详细信息
   git remote rm 主机名：删除远程主机
   git remote rename 机原主名 新主机名：对远程主机的改名
### 11、git reflog：查看当前仓库执行过的操作的日志，会显示当前仓库所有操作和对应的哈希值，可以使用下面命令
   git reset --hard 哈希值：推进至历史的某个状态
### 12、git pull：获取最新的远程仓库分支
   git pull 主机名 远程分支名称：本地分支名称：  从远程仓库获取最新的此分支的最新状态与本地的分支合并。
### 13、git push:将本地分支的更新，推送到远程主机。
   git push 主机名 本地分支名称：远程主机名称：  将本地仓库的某个分支与远程主机的某个分支合并。
### 14、git clone 版本库地址：直接从远程仓库下载一个新的项目(本地没有此项目)
   该命令会在本地主机生成一个目录，与远程主机的版本库同名。
   $ git clone https://github.com/WangJieWJ/IntelliJ-IDEA.git
   如果要指定不同的目录名，可以将目录名作为git clone命令的第二个参数。
   $ git clone https://github.com/WangJieWJ/IntelliJ-IDEA.git download
### 15、git fetch 远程主机：取回该远程主机中的所有分支的更新到本地
   git fetch 远程主机名 分支名：取回该远程主机中的特定分支的更新。

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
   
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">

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
</project>


## IntelliJ IDEA学习

### 使用IntelliJ IDEA来新建一个使用Maven管理的一个WebApp项目，并使用git来提交到GitHub中。
   具体项目见GitHub地址：https://github.com/WangJieWJ/IntelliJ-IDEA.git
   
### 在IntelliJ IDEA中配置git：
   1、选择File中的Setting
   2、Version Control中的git，选择Path to Git executable中选择git bin目录下的git.exe

### 在IntelliJ IDEA中配置Maven：
   1、选择File中的Setting
   2、Build,Execution,Deployment---->Build Tools---->Maven,右侧中的Maven home directory选择安装的目录。
   
### 在IntelliJ IDEA中配置Tomcat：
   1、选择File中的Setting
   2、Build,Execution,Deployment---->Deployment---->Application Servers,点击添加按钮，添加Tomcat的安装目录。
   
### 创建使用Maven管理的WabApp项目：
  1、新建项目New Project
  2、选择Java Enterprise，并在右侧选择合适的Java EE版本、Application Server、并在下面的Additional Libraries and Framrworks中选择Web Application。
  3、之后再输入项目的名称等基础信息。
   

   
   
   
   
 




