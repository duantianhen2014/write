## ubuntu下PHP7.2安装ImageMagick

### 采用pear方式安装

I. 安装ImageMagick

```csharp
sudo apt-get install imagemagick
```

II. 安装imagemagick 的lib 供php调用

```csharp
sudo apt-get install libmagick++-dev
```

III. 调用当前的pecl安装imagick

```undefined
pecl install imagick
```

IV. 修改php.ini.重启nginx服务器

在php.ini中添加: `extension = imagick.so`

PS：当提示`Please provide the prefix of Imagemagick installation [autodetect] :`直接按Enter