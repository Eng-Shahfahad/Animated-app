import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Animated App',
      theme: ThemeData(
        useMaterial3: true,
        colorScheme: ColorScheme.fromSeed(
          seedColor: Colors.deepPurple,
        ),
      ),
      home: const WelcomeScreen(),
    );
  }
}

class WelcomeScreen extends StatefulWidget {
  const WelcomeScreen({super.key});

  @override
  State<WelcomeScreen> createState() => _WelcomeScreenState();
}

class _WelcomeScreenState extends State<WelcomeScreen> {
  bool isAnimated = false;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.deepPurple.shade50,

      appBar: AppBar(
        title: const Text(
          "Flutter Animation",
          style: TextStyle(color: Colors.white),
        ),
        centerTitle: true,
        backgroundColor: Colors.deepPurple,
      ),

      body: Center(
        child: AnimatedContainer(
          duration: const Duration(milliseconds: 700),
          curve: Curves.easeInOut,

          width: isAnimated ? 340 : 280,
          padding: const EdgeInsets.all(25),

          decoration: BoxDecoration(
            color: isAnimated ? Colors.deepPurple : Colors.white,
            borderRadius: BorderRadius.circular(25),
            boxShadow: const [
              BoxShadow(
                blurRadius: 15,
                color: Colors.black26,
                offset: Offset(0, 8),
              ),
            ],
          ),

          child: Column(
            mainAxisSize: MainAxisSize.min,
            children: [

              AnimatedRotation(
                turns: isAnimated ? 1 : 0,
                duration: const Duration(milliseconds: 700),

                child: CircleAvatar(
                  radius: isAnimated ? 55 : 45,
                  backgroundColor: Colors.orange,
                  child: const Icon(
                    Icons.person,
                    size: 55,
                    color: Colors.white,
                  ),
                ),
              ),

              const SizedBox(height: 20),

              Text(
                isAnimated
                    ? "🎉 Welcome Shah Fahad!"
                    : "Welcome Shah Fahad",
                style: TextStyle(
                  fontSize: 30,
                  fontWeight: FontWeight.bold,
                  color:
                  isAnimated ? Colors.white : Colors.deepPurple,
                ),
              ),

              const SizedBox(height: 10),

              Text(
                isAnimated
                    ? "You clicked the button!"
                    : "Press the button below.",
                textAlign: TextAlign.center,
                style: TextStyle(
                  fontSize: 18,
                  color:
                  isAnimated ? Colors.white70 : Colors.black54,
                ),
              ),

              const SizedBox(height: 30),

              ElevatedButton(
                onPressed: () {
                  setState(() {
                    isAnimated = !isAnimated;
                  });
                },
                style: ElevatedButton.styleFrom(
                  backgroundColor: isAnimated
                      ? Colors.orange
                      : Colors.deepPurple,
                  foregroundColor: Colors.white,
                  padding: const EdgeInsets.symmetric(
                    horizontal: 35,
                    vertical: 15,
                  ),
                ),
                child: Text(
                  isAnimated
                      ? "Reset"
                      : "Animate",
                  style: const TextStyle(fontSize: 18),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
