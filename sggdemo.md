# SGG Progress
1. 读取游戏客户端数据，和屏幕截图

2. 对照客户端数据和游戏渲染画面，手动标注Objects和Relationships数据，生成JSON文件
   ![](https://github.com/renchengkai/sggdata-prepare/blob/master/bbox.jpg)

3. 根据标注数据JSON文件，生成SGG训练所需格式

4. 完成训练SGG模型（算法IMP）

   ![](https://github.com/renchengkai/sggdata-prepare/blob/master/sggdet.png)
   ~~~
   **************************************************
    box_labels 0: orbitalcommand; score: 0.997576892375946
    box_labels 1: stalker; score: 0.9975283741950989
    box_labels 2: supplydepotlowered; score: 0.9968454241752625
    box_labels 3: labmineralfield; score: 0.994364857673645
    box_labels 4: scv; score: 0.9908389449119568
    box_labels 5: scv; score: 0.990374743938446
    box_labels 6: labmineralfield; score: 0.9858909845352173
    box_labels 7: scv; score: 0.9839937686920166
    box_labels 8: supplydepotlowered; score: 0.976327657699585
    box_labels 9: scv; score: 0.9655444622039795
    box_labels 10: scv; score: 0.962700366973877
    box_labels 11: probe; score: 0.9571759700775146
    box_labels 12: factory; score: 0.9519650936126709
    box_labels 13: scv; score: 0.9466681480407715
    box_labels 14: barracks; score: 0.9397025108337402
    box_labels 15: scv; score: 0.9371788501739502
    box_labels 16: probe; score: 0.9357345104217529
    box_labels 17: scv; score: 0.9334496855735779
    box_labels 18: starport; score: 0.8996061682701111
    box_labels 19: barracks; score: 0.8902183175086975
    box_labels 20: scv; score: 0.8820248246192932
    box_labels 21: stalker; score: 0.8514573574066162
    box_labels 22: drone; score: 0.8505644202232361
    box_labels 23: labmineralfield; score: 0.8475717902183533
    box_labels 24: labmineralfield; score: 0.8473016023635864
    box_labels 25: scv; score: 0.8094367980957031
    box_labels 26: drone; score: 0.7754738330841064
    box_labels 27: scv; score: 0.7345299124717712
    box_labels 28: stalker; score: 0.73261559009552
    box_labels 29: richmineralfield; score: 0.7186293005943298
    **************************************************
    rel_labels 0: 9_scv => attack => 18_starport; score: 0.258664071559906
    rel_labels 1: 26_drone => mining => 6_labmineralfield; score: 0.11217576265335083
    rel_labels 2: 1_stalker => attack => 21_stalker; score: 0.06559959799051285
    rel_labels 3: 28_stalker => attack => 21_stalker; score: 0.036217473447322845
    rel_labels 4: 13_scv => mining => 6_labmineralfield; score: 0.03577889874577522
    rel_labels 5: 5_scv => attack => 21_stalker; score: 0.0291718989610672
    rel_labels 6: 27_scv => mining => 6_labmineralfield; score: 0.014038337394595146
    rel_labels 7: 4_scv => attack => 21_stalker; score: 0.007429279386997223
    rel_labels 8: 26_drone => attack => 21_stalker; score: 0.0045816791243851185
    rel_labels 9: 11_probe => mining => 6_labmineralfield; score: 0.0039389305748045444
    rel_labels 10: 21_stalker => attack => 1_stalker; score: 0.0037213985342532396
    rel_labels 11: 22_drone => deliver => 0_orbitalcommand; score: 0.003402718808501959
    rel_labels 12: 20_scv => attack => 11_probe; score: 0.0020148654002696276
    rel_labels 13: 9_scv => build => 19_barracks; score: 0.0019606612622737885
    rel_labels 14: 27_scv => build => 29_richmineralfield; score: 0.0018819421529769897
    rel_labels 15: 22_drone => attack => 11_probe; score: 0.0018384542781859636
    rel_labels 16: 21_stalker => attack => 28_stalker; score: 0.0013068875996395946
    rel_labels 17: 4_scv => mining => 23_labmineralfield; score: 0.0009160112822428346
    rel_labels 18: 26_drone => attack => 11_probe; score: 0.0008279106114059687
    rel_labels 19: 13_scv => attack => 21_stalker; score: 0.0007335791015066206
   ~~~
