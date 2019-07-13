# windows10下Node.js及设置

1. 官网下载Node.js安装包

   [Node.js官网地址](https://nodejs.org/en/)

   选择LTS（长期维护）版

2. 安装

   next -> next就行（安装目录可自行选择）

3. 配置npm（可选）
   我们需要配置npm的全局模块的存放路径以及cache的路径，例如我希望将以上两个文件夹放在NodeJS的主目录下，便在NodeJs下建立“node_global”及“node_cache”两个文件夹。我们就在cmd中键入两行命令：

   ```shell
   npm config set prefix "D:\Program Files\nodejs\node_global"
   npm config set cache "D:\Program Files\nodejs\node_cache"
   ```

4. 换淘宝镜像

   ```shell
   npm config set registry https://registry.npm.taobao.org
   ```

5. 安装cnpm（可选）

   此时需要在环境变量Path路径后面加上D:\Program Files\nodejs\node_global，即cnpm脚本命令所在的文件夹目录下。

6. npm命令
   使用npm安装插件：命令提示符执行 

   ```shell
   npm install <name> [-g][--save-dev]
   ```

   使用npm卸载插件：

   ```shell
   npm uninstall <name> [-g][--save-dev] 
   ```

   PS：不要直接删除本地插件包 

   使用npm更新插件：

   ```shell
   npm update <name> [-g][--save-dev] 
   ```

   更新全部插件：

   ```shell
   npm update [--save-dev] 
   ```

   查看npm帮助：

   ```shell
   npm help 
   ```

   查看当前目录已安装插件：

   ```shell
   npm list
   ```

   注：cnpm跟npm用法完全一致，只是在执行命令时将npm改为cnpm。

   解释
   <name>为Node插件名称；

   [-g]：全局安装；将会安装在C:\Users\Administrator\AppData\Roaming\npm，并且写入系统环境变量，若操作了第三步，此处将在node_global那个目录下； 

   非全局安装：将会安装在当前定位目录； 全局安装可以通过命令行在任何地方调用它，本地安装将安装在定位目录的node_modules文件夹下，通过require()调用；

   --save：将保存配置信息至package.json（package.json是nodejs项目配置文件）；

   -dev：保存至package.json的devDependencies节点，不指定-dev将保存至dependencies节点；

   因为node插件包相对来说非常庞大，所以不加入版本管理，将配置信息写入package.json并将其加入版本管理，其他开发者对应下载即可，所以需保存至package.json中（命令提示符执行npm install，则会根据package.json下载所有需要的包）。

7. 比较实用的一些插件和命令

   删除本地node_module的命令

   安装： npm install rimraf -g
   执行： rimraf node_modules

   自动重启NodeJs后台服务器的命令:

   安装：npm install -g nodemon

   执行：nodemon server.js 