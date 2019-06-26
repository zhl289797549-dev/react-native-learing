React Native 0.59


示例教程：Hello World：https://reactnative.cn/docs/tutorial/
	1、使用 React Native 命令行工具来创建一个名为"HelloWorldProject"的新项目：
		react-native init HelloWorldProject
    2、编译并运行 React Native 应用
	   cd HelloWorldProject
	   react-native run-android
	   出现问题：参考AwesomeProject
	   
	   修改根目录app.js 
	   ========================================================================
	   import React, { Component } from 'react';
	   import { Text, View } from 'react-native';

		export default class HelloWorldApp extends Component {
		  render() {
			return (
				<View style={{ flex: 1, justifyContent: "center", alignItems: "center" }}>
				  <Text>Hello, world!</Text>
				</View>
			);
		  }
		}
		========================================================================
		保存运行react-native run-android 发现没有生效页面还是Welcome to React Native！
		原因是bundle文件没有重新生成还是旧的，所以要先运行
		react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res
		这个命令重新生成bundle 然后运行react-native run-android 页面就出现Hello,world!
	3、修改js文件后自动运行
       问题：如果每次修改都像第2步骤重新打包运行，效率未免太低。
       解决：1、项目根目录运行react-native start --port=8088 指定端口号运行react-native 监听js文件的修改
	   react-native默认端口号是8081 如果被占用了就要更换端口号
	   2、adb reverse tcp:8088 tcp:8088  根改手机的tcp端口
	   3、手机menu 键弹出 react-native 菜单 选择 Dev Settings-> Debug server host & port for device
	      输入localhost:8088
	   4、修改app.js 保存后，手机中运行menu->reload 就可以马上看到效果了
	   5、省略menu->reload步骤 打开menu->enable live reload 运行实时加载 这样电脑js文件已修改，结果就马上呈现到手机端了。
		

		
	   
			
   
