https://github.com/google/oboe/blob/ec8de0feef6df0af28d8de1d85437e2b7620c92e/samples/RhythmGame/src/main/java/com/google/oboe/sample/rhythmgame/GameSurfaceView.java

```
  @Override
    public boolean onTouchEvent(MotionEvent e) {
        // MotionEvent reports input details from the touch screen
        // and other input controls. In our case we care about DOWN events.
        switch (e.getAction()) {
            case MotionEvent.ACTION_DOWN:
                native_onTouchInput(0, e.getEventTime(), (int)e.getX(), (int)e.getY());
                break;
        }
        return true;
    }
```

https://github.com/google/oboe/blob/06fd9bf1c37c23e89737588351f62e2acde34f73/samples/RhythmGame/src/main/cpp/native-lib.cpp

```
JNIEXPORT void JNICALL
Java_com_google_oboe_sample_rhythmgame_GameSurfaceView_native_1onTouchInput(JNIEnv *env,
                                                                            jclass type,
                                                                            jint event_type,
                                                                            jlong time_since_boot_ms,
                                                                            jint pixel_x,
                                                                            jint pixel_y) {
    game->tap(time_since_boot_ms);
}
```
