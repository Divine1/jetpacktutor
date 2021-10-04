dropdown box

```
package com.tadvice.tripadvisorjc1.screens;

import android.os.Build.VERSION.SDK_INT
import android.util.Log
import android.view.Menu
import androidx.compose.foundation.*

import androidx.compose.foundation.layout.*
import androidx.compose.foundation.lazy.LazyColumn
import androidx.compose.material.*
import androidx.compose.material.icons.Icons
import androidx.compose.material.icons.filled.Add
import androidx.compose.runtime.Composable
import androidx.compose.runtime.mutableStateOf
import androidx.compose.runtime.remember
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.platform.LocalContext
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import coil.ImageLoader
import coil.compose.rememberImagePainter
import coil.decode.GifDecoder
import coil.decode.ImageDecoderDecoder
import com.tadvice.tripadvisorjc1.R
import com.tadvice.tripadvisorjc1.ui.theme.Tripadvisorjc1Theme

@Composable
fun ViewAllTrips() {
    //Text(text = "View all trips - items")

    Scaffold(
        bottomBar = {
            CustomBottombar()
        }
    ) {

        DropdownDemo()
    }
}

@Composable
fun DropdownDemo() {
    var expanded = remember { mutableStateOf(false) }
    val items = listOf("A", "B", "C", "D", "E", "F")
    var selectedIndex = remember { mutableStateOf(0) }


    Column(
        //modifier = Modifier.border(BorderStroke(1.dp, Color.Blue))
    ) {
        Button(onClick = {
            expanded.value = true
        }) {
            Text(
                text="Click here",
                //modifier = Modifier.size(100.dp,20.dp)
            )
        }

        Box(modifier = Modifier.width(50.dp)) {

            DropdownMenu(
                expanded = expanded.value,
                onDismissRequest = { expanded.value = false },
                modifier = Modifier
                    .background(
                        Color.Red
                    )
            ) {
                items.forEachIndexed { index, s ->
                    DropdownMenuItem(onClick = {
                        selectedIndex.value = index
                        expanded.value = false
                    }) {
                        Text(text = s )
                    }
                }
            }
        }
       // Text(text = items.get(selectedIndex.value ))
    }
}

@Composable
fun renderGif(imageData : Int,imageLoader:ImageLoader,label : String){
    Image(painter = rememberImagePainter(
        data = imageData,
        imageLoader = imageLoader
    ), contentDescription = label,
        modifier = Modifier.size(400.dp)
    )
}

@Composable
fun CustomBottombar(){
    //  Icon(bitmap = painterResource(id = R.drawable.ic_baseline_add_24), contentDescription = "Create Trip" )
    //Icon(imageVector = Icons.Default.Add, contentDescription ="" )
    Surface(
        modifier = Modifier.fillMaxWidth()
    ) {
        Row(

            horizontalArrangement = Arrangement.Center
        ) {
            Button(onClick = {
                Log.d("ViewAllTrips","button clicked")
            }) {
                Icon(imageVector = Icons.Default.Add, contentDescription ="" )
            }
        }
    }


}

@Preview(showBackground = true)
@Composable
fun DefaultPreview() {
    Tripadvisorjc1Theme {
        //Greeting("Android")

        ViewAllTrips()
    }
}
```
