# bot-guide-by-guitar


ต้องมี server ก่อน อาจจะ regis aws ก็ได้เพราะฟรี 1 ปี


ละก็มาแก้ line นี้

```
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
  }

  @override
  bool shouldRepaint(_SuccessPainter oldDelegate) {
    return oldDelegate.scale != scale || oldDelegate.color != color;
  }
}
```
