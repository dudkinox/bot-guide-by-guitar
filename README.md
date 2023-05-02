# bot-guide-by-guitar


ต้องมี server ก่อน อาจจะ regis aws ก็ได้เพราะฟรี 1 ปี


ละก็มาแก้ line นี้

```
<<<<<<< HEAD
import 'package:flutter/material.dart';
import 'package:vector_math/vector_math.dart' as vector;

class SuccessAnimation extends StatefulWidget {
  final double size;
  final Color color;

  const SuccessAnimation({Key? key, required this.size, required this.color})
      : super(key: key);

  @override
  _SuccessAnimationState createState() => _SuccessAnimationState();
}

class _SuccessAnimationState extends State<SuccessAnimation>
    with SingleTickerProviderStateMixin {
  late AnimationController _controller;
  late Animation<double> _scaleAnimation;

  @override
  void initState() {
    super.initState();

    _controller = AnimationController(
      vsync: this,
      duration: const Duration(milliseconds: 500),
    )..addListener(() {
        setState(() {});
      });

    _scaleAnimation = Tween<double>(begin: 0.0, end: 1.0).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Curves.elasticOut,
      ),
    );

    _controller.forward();
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return CustomPaint(
      size: Size(widget.size, widget.size),
      painter: _SuccessPainter(
        scale: _scaleAnimation.value,
        color: widget.color,
      ),
    );
  }
}

=======
>>>>>>> c07a125 (Update README.md)
class _SuccessPainter extends CustomPainter {
  final double scale;
  final Color color;

  _SuccessPainter({required this.scale, required this.color});

  @override
  void paint(Canvas canvas, Size size) {
    final center = Offset(size.width / 2, size.height / 2);

    final circleRadius = size.width / 2;
    final circlePaint = Paint()
      ..color = color
      ..style = PaintingStyle.fill;
    canvas.drawCircle(center, circleRadius * scale, circlePaint);

<<<<<<< HEAD
    final tickPaint = Paint()
      ..color = Colors.white
      ..style = PaintingStyle.stroke
      ..strokeWidth = circleRadius * 0.2
      ..strokeCap = StrokeCap.round;

    final path = Path();
    final start = Offset(size.width * 0.35, size.height * 0.6);
    final control1 = Offset(size.width * 0.45, size.height * 0.8);
    final end = Offset(size.width * 0.75, size.height * 0.4);
    path.moveTo(start.dx, start.dy);
    path.quadraticBezierTo(control1.dx, control1.dy, end.dx, end.dy);

    canvas.drawPath(path, tickPaint);
=======
    final iconSize = circleRadius * 0.8 * scale;
    final icon = Icon(
      Icons.check,
      size: iconSize,
      color: Colors.white,
    );

    final iconOffset = Offset(
      size.width / 2 - iconSize / 2,
      size.height / 2 - iconSize / 2,
    );

    canvas.drawCircle(center, circleRadius * scale, circlePaint);
    canvas.drawIcon(icon.icon, iconOffset, icon.color, scale * iconSize);
>>>>>>> c07a125 (Update README.md)
  }

  @override
  bool shouldRepaint(_SuccessPainter oldDelegate) {
    return oldDelegate.scale != scale || oldDelegate.color != color;
  }
}
<<<<<<< HEAD

=======
>>>>>>> c07a125 (Update README.md)
```
