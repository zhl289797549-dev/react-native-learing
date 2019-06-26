React Native 0.59


搭建开发环境：https://reactnative.cn/docs/getting-started/
	1、使用 React Native 命令行工具来创建一个名为"AwesomeProject"的新项目：
		react-native init AwesomeProject
    2、编译并运行 React Native 应用
	   cd AwesomeProject
	   react-native run-android
	   问题：Android手机中出现红屏错误提示：Unable to load script.Make sure you're either
	   running a Metro server(run 'react-native start') or that your bundle 'index.android.bundle' 
	   is packaged correctly for release
	   描述：打包出现问题，类似bundle.js的文件没有生成，导致运行失败。
	   解决:cd 项目根目录/android/app/src/main/  发现没有assets文件夹，创建assets文件夹
	        然后cd 到项目根目录 android ./gradlew clean 运行gradlew 清理android项目目录重新编译
			然后运行命令：
			react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res
			这个命令作用是重新生成bundle文件 运行后 项目根目录/android/app/src/main/assets/ 就出现文件了
			再次运行 react-native run-android 项目运行正常。手机出现Welcome to React Native！
			
   
