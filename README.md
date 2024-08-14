import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return  MaterialApp(
      theme: ThemeData(
        appBarTheme: AppBarTheme(
          backgroundColor: Colors.green[400],
          titleTextStyle: const TextStyle(color: Colors.white,fontSize: 20,fontWeight: FontWeight.w500),

        ),
        elevatedButtonTheme: ElevatedButtonThemeData(
          style: TextButton.styleFrom(
            backgroundColor: Colors.green[100],
            foregroundColor: Colors.green[900]
          )
        )
      ),
      debugShowCheckedModeBanner: false,
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatefulWidget {
   MyHomePage({super.key});

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {

  void showAlertDialogue(BuildContext context) {
    showDialog(context: context, builder: (BuildContext) {
      return AlertDialog(
        shape: RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(16)
        ),
        title: const Text("Sample"),
        content: const Text("This alert dialogue only for practice",
          style: TextStyle(fontSize: 16),),
        actions: [
          TextButton(onPressed: () {
            Navigator.of(context).pop();
          },
              child: const Text("Yes")),
        ],
      );
    });
  }

  void showBottom(BuildContext context,) {
    showModalBottomSheet(
        shape: RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(12)
        ),
        backgroundColor: Colors.white,
        context: context, builder: (BuildContext) {
      return const SizedBox(
        height: 200,
        width: double.infinity,
          child: Padding(
            padding: EdgeInsets.all(16.0),
            child: Column(
              children: [
                Text("Choose",style: TextStyle(fontSize: 18,fontWeight: FontWeight.bold),)
              ],
            ),
          ),
      );
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text("Home"),
          centerTitle: true,
        ),
        body:Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              const Text("Flutter Text Styling",
                style: TextStyle(fontSize: 24,fontWeight: FontWeight.bold,),),
              const SizedBox(height: 24,),
              const Text("Experiment with text styles",style:
              TextStyle(fontStyle: FontStyle.italic,fontSize: 20),),
              const SizedBox(height: 16,),
               TextButton(onPressed: (){
                 ScaffoldMessenger.of(context).showSnackBar(
                   const SnackBar(
                     content: Text('You clicked the button!'),
                   ),
                 );
               }, child: const Text("Click Me")),
              const SizedBox(height: 8,),
              const Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  Text("Welcome to",style: TextStyle(fontSize: 19,fontWeight: FontWeight.w500),),
                  SizedBox(width: 8,),
                  Text("Flutter!",style: TextStyle(fontSize:19,fontWeight: FontWeight.w500,color: Colors.blue ),),
                ],
              )
            ],
          ),
        )
    );
  }
}

