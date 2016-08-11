# Pull-To-Refersh-Android

#Requirement for Activity :

public int generateRandomNumber()
    {
        java.util.Random random = new java.util.Random();
        int ran = random.nextInt(10-1+1)+1;
        return ran;
    }

    public void initShowPull()
    {
        final SwipeRefreshLayout swipeRefreshLayout = (SwipeRefreshLayout) findViewById(R.id.content_mainSwipe);
        final TextView randomTV = (TextView) findViewById(R.id.randomTV);

        randomTV.setText(String.valueOf(generateRandomNumber()));


        swipeRefreshLayout.setColorSchemeColors(Color.RED, Color.GREEN, Color.BLUE, Color.GRAY);
        //swipeRefreshLayout.setColorSchemeColors(android.R.color.holo_blue_dark, android.R.color.holo_blue_light, android.R.color.holo_green_light, android.R.color.holo_green_dark);

        swipeRefreshLayout.setOnRefreshListener(new SwipeRefreshLayout.OnRefreshListener() {
            @Override
            public void onRefresh() {
                swipeRefreshLayout.setRefreshing(true);

                randomTV.setText(String.valueOf(generateRandomNumber()));

                swipeRefreshLayout.setRefreshing(false);

            }
        });
    }


#Requirement for xml :

<?xml version="1.0" encoding="utf-8"?>
<android.support.v4.widget.SwipeRefreshLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/content_mainSwipe"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    app:layout_behavior="@string/appbar_scrolling_view_behavior"
    tools:context="com.amitupadhyay.pulltorefersh.MainActivity"
    tools:showIn="@layout/app_bar_main">


    <ScrollView
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:orientation="vertical">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Random Number : "
                android:textSize="25sp"/>

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/randomTV"
                android:layout_marginBottom="20dp"
                android:layout_marginTop="20dp"
                android:textSize="25sp"
                android:textStyle="bold"/>


            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="Pull To Generate Random Number"
                android:textSize="20sp"
                android:textColor="#ffffff"
                android:background="#026466"/>

        </LinearLayout>

    </ScrollView>

</android.support.v4.widget.SwipeRefreshLayout>

#-Amit Upadhyay
