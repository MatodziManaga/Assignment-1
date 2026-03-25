# Assignment-1
Repo for Assignment 1 submissions
MainActivity.kt

package com.example.assignment

import android.annotation.SuppressLint
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import android.widget.Toast
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat
class MainActivity : AppCompatActivity() {
    private lateinit var editTextTimeOfDay: EditText
    private lateinit var buttonGetSuggestion: Button
    private lateinit var textViewSuggestion: TextView
    private lateinit var buttonReset: Button
    @SuppressLint("MissingInflatedId", "SetTextI18n")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main)) { v, insets ->
            val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom)
            insets
        }
        //Initialize views
        editTextTimeOfDay = findViewById(R.id.editTextTimeOfDay)
        buttonGetSuggestion = findViewById(R.id.buttonGetSuggestion)
        textViewSuggestion = findViewById(R.id.textViewSuggestion)
        buttonReset = findViewById(R.id.buttonReset)

        //set up onClick listener for Get Suggestion button
        buttonGetSuggestion.setOnClickListener {
            val timeOfDay = editTextTimeOfDay.text.toString().trim().lowercase()

            //Get suggestion based on input time of day
            val suggestion = getSocialSparkstion(timeOfDay)

            if (suggestion.isNotEmpty()){
                textViewSuggestion.text = suggestion
            } else {
                Toast.makeText(this,"Please enter a valid time of day (Morning,Afternoon,etc.)",
                    Toast.LENGTH_SHORT).show()
            }
        }
        //Set up onClick listener for Reset button
        buttonReset.setOnClickListener {
            editTextTimeOfDay.text.clear()
            textViewSuggestion.text = "Suggestion will appear here"

        }
    }
    //function to provide a suggestion based on the input time of day
    private  fun getSocialSparkstion (timeOfDay: String): String {
        return when (timeOfDay) {
            "morning" -> "Send a 'Good morning' text to a family member."
            "mid-morning" -> "Reach out to a colleague with a quick 'Thank you."
            "afternoon" -> "Share a funny meme or interesting link with a friend."
            "afternoon snack time" -> "Send a quick 'thinking of you' message."
            "dinner" -> "Call a friend or relative for a 5-minute catch-up."
            "after dinner","night"-> "Leave a thoughtful comment on a friend's post."
            else -> "" //Return empty if invalid input
        }
    }
}









activity_nain.xml

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#CDDC39"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/editTextTimeOfDay"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="100dp"
        android:layout_marginEnd="101dp"
        android:layout_marginBottom="120dp"
        android:ems="10"
        android:inputType="text"
        android:text="Name"
        android:textColor="#FD0505"
        android:textSize="24sp"
        app:layout_constraintBottom_toTopOf="@+id/textViewSuggestion"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

    <TextView
        android:id="@+id/textViewSuggestion"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="156dp"
        android:layout_marginEnd="178dp"
        android:layout_marginBottom="232dp"
        android:text="Display"
        android:textColor="#F60707"
        android:textSize="34sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

    <Button
        android:id="@+id/buttonReset"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginTop="251dp"
        android:layout_marginEnd="19dp"
        android:layout_marginBottom="62dp"
        android:text="Reset"
        android:textSize="24sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/buttonGetSuggestion"
        app:layout_constraintTop_toBottomOf="@+id/editTextTimeOfDay" />

    <Button
        android:id="@+id/buttonGetSuggestion"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="27dp"
        android:layout_marginTop="251dp"
        android:layout_marginEnd="120dp"
        android:layout_marginBottom="62dp"
        android:text="Submit"
        android:textSize="24sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/buttonReset"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editTextTimeOfDay" />

    <ImageView
        android:id="@+id/imageView3"
        android:layout_width="330dp"
        android:layout_height="159dp"
        android:layout_marginStart="40dp"
        android:layout_marginTop="106dp"
        android:layout_marginEnd="41dp"
        android:layout_marginBottom="37dp"
        app:layout_constraintBottom_toTopOf="@+id/editTextTimeOfDay"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="1.0"
        app:srcCompat="@drawable/_493803" />
  </androidx.constraintlayout.widget.ConstraintLayout>











