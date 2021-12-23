1.ファイルの使い方

  使用しているワークスペース内にあるソースファイルのディレクトリへコピーし，必要なライブラリをインストールした後にcatkin_make（またはcatkin build）してください．

2.ワークスペースが~/catkin_ws/の場合
	1.ROSを使ったマニピュレータの制御（例：6自由度ロボットアームの場合）
		1.ロボットアームのシミュレーション起動コマンド例
		　起動したRviz上で6軸ロボットアームの動作シミュレーションを確認する．
			$ cd ~/catkin_ws
			$ catkin build
			$ source devel/setup.bash
			$ roslaunch sixdofarm_moveit_config demo.launch

	2.差動型の移動ロボット制御と地図構築，ナビゲーション
	
		1.差動２輪移動ロボットの遠隔操作による移動コマンド例
		　作成した差動2輪移動ロボットのシミュレーションをRviz上で立ち上げて，キーボードの入力により移動ロボットを制御する．
			１つ目のターミナル
			$ roslaunch diff_mobile_robot diff_mobile_robot.launch
			２つ目のターミナル
			$ roslaunch diff_mobile_robot diff_mobile_gazebo.launch
			３つ目のターミナル
			$ rosrun diff_mobile_robot key_teleop.py

			キーボードのコマンド例（defaultの場合）
			  なお，2つ目のターミナルを最前面にした状態のみ操作できる．
			"w"：前進　　"x"：後退　　"s"：停止　　"a"：左旋回　　"d"：右旋回
			"g"：終了（※ctl+cを押しても終了しないので注意）

		2.Gmappingを用いた地図生成・保存コマンド例
		　動力学シミュレーション”Gazebo”上において，差動2輪移動ロボットを走行させることで，地図を構築する．
			1つ目のターミナル
			$ roslaunch diff_mobile_robot diff_mobile_gazebo.launch
			2つ目のターミナル
			$ roslaunch diff_mobile_robot gmapping.launch
			3つ目のターミナル
			$ rosrun diff_mobile_robot key_teleop.py
			4つ目のターミナル（構築した地図の保存）
			$ cd ~/catkin_ws/src/diff_mobile_robot/map
			$ rosrun map_server map_saver -f testmap

		3.AMCLによる移動ロボットの自己位置推定コマンド例
		　2.Gmappingで生成した地図において，差動2輪移動ロボットのナビゲーションを行う．
			($ sudo apt-get install ros-kinetic-amcl)
			($ sudo apt-get install ros-melodic-amcl)
			1つ目のターミナル
			$ roslaunch diff_mobile_robot diff_mobile_gazebo.launch
			2つ目のターミナル
			$ roslaunch diff_mobile_robot amcl.launch
			3つ目のターミナル
			$ rviz rviz



