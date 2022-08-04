### クリック処理①（OnClickListenerを使用）
MainActivity.java
```java
public class MainActivity extends AppCompatActivity implements View.OnClickListener {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        //ボタンのIDからボタンを探し、buttonクラスにセットする
        final Button button1 = findViewById(R.id.button1);
        //処理を行うclassをsetOnClickListenerにセットする（thisはView.OnClickListenerをimplementsしたMainActivityのこと）
        button1.setOnClickListener(this);

        final Button button2 = findViewById(R.id.button2);
        button1.setOnClickListener(this);

        final Button button3 = findViewById(R.id.button3);
        button1.setOnClickListener(this);
    }

    public void onClick(View view) {
        //クリックされたボタンのIDを取得して、分岐処理
        if(view.getId() == R.id.button1) {
            Log.d("button1","button1が押されました");
        } else if(view.getId() == R.id.button2) {
            Log.d("button2","button2が押されました");
        } else {
            Log.d("button3","button3が押されました");
        }
    }
}
```

### クリック処理②（変数を使用）
MainActivity.java
```java
package com.example.develop;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        //ボタンのIDからボタンを探し、buttonクラスにセットする
        final Button button1 = findViewById(R.id.button1);
        //処理を行うclassをsetOnClickListenerにセットする
        button1.setOnClickListener(buttonClick);

        final Button button2 = findViewById(R.id.button2);
        button1.setOnClickListener(buttonClick);

        final Button button3 = findViewById(R.id.button3);
        button1.setOnClickListener(buttonClick);
    }

    private View.OnClickListener buttonClick = new View.OnClickListener() {
        @Override
        public void onClick(View view) {
            switch (view.getId()) {
                case R.id.button1:
                    Log.d("debug","button1, Perform action on click");
                    break;
                case R.id.button2:
                    Log.d("debug","button2, Perform action on click");
                    break;
                case R.id.button3:
                    Log.d("debug","button3, Perform action on click");
                    break;
            }
        }
    };
}
```

### 画面遷移
MainActivity.java
```Java
//
setContentView(R.layout.layoutフォルダのxmlの名前);
例）setContentView(R.layout.example);  layout/example.xmlの場合
```

### 画面遷移（Intentを使用する場合）
MainActivity.java
```Java
Intent intent = new Intent(this,クラス名.class);
startActivity(intent);

//よくメソッド内で使われる
public void onClick(View view) {
  Intent intent = new Intent(this,example.class);
  startActivity(intent);
}
```

### 画面遷移（Intentで値を渡す）
MainActivity.java
```Java
//渡すクラス
Intent intent = new Intent(this,クラス名.class);
intent.putExtra(key, values);   //例） putExtra("name", "太郎")
startActivity(intent);

//受け取る側
Intent intent = getIntent();
String person = intent.getStringExtra(key);  //例） getStringExtra("name")
      //boolean型：getBooleanExtra()
      //int型：getIntExtra()
```

### TextViewに値を入れて表示する
MainActivity.java
```java
txt = (TextView)this.findViewById(R.id.textViewのID);
txt.setText("入れたい値");
```