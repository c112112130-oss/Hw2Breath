# Hw2Breath
1.修正 gettingDark 狀態的轉換條件：
原來的程式中，gettingDark 狀態下是依賴 upbnd2 來進行轉換，這邊的條件不正確，應該是要根據 upbnd1 來判斷是否達到最暗的狀態。因此，我將 upbnd2 = "0000"&"0000" 改成 upbnd1 = "0000"&"0000"，這樣就能正確地從最暗回到最亮。

2.初始化 alreadyP_PWM_cycles 信號：
在原來的程式中，alreadyP_PWM_cycles 並沒有在重置時設為 '0'。我在修改後的程式中，將它初始化為 '0'，確保在每次重置後，PWM計數能夠正確開始。

3.改善 PWM 計數過程：
原程式在 P_PWM_cycles 過程中，當 pwm_pedge 信號為 1 時，並沒有正確處理 PWM 計數，可能會導致 pwmCnt 計數不正確。我加入了條件檢查，只有當 pwm_pedge = '1' 時才會進行計數，並且達到 P (設定為 3) 時會重置。

4.設置 o_led 輸出：
在修改後的程式中，我加上了 o_led <= pwm;，讓輸出 o_led 可以直接根據 pwm 信號來顯示，這是之前程式中缺少的部分。
