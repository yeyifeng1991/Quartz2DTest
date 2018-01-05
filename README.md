# Quartz2DTest
绘制简单的圆形
简单步骤如下
```
   // 方法1   UIGraphicsBeginImageContext(<#CGSize size#>);
// 1.创建上下文
    UIGraphicsBeginImageContextWithOptions(CGSizeMake(200, 200), NO, 0);
    /*
     //方法2 UIGraphicsBeginImageContextWithOptions(CGSize size, BOOL opaque, CGFloat scale)
     
     使用两个方法同样都可以创建，但是使用第一个方法将来创建的图片清晰度和质量没有第二种方法的好。
     方法2接收三个参数：
     CGSize size：指定将来创建出来的bitmap的大小
     
     BOOL opaque：设置透明YES代表透明，NO代表不透明
     
     CGFloat scale：代表缩放,0代表不缩放
     
     创建出来的bitmap就对应一个UIImage对象
     
     */
    // 2.获取上下文
    CGContextRef ctx = UIGraphicsGetCurrentContext();
    // 3. 绘制一个圆形
    CGContextAddEllipseInRect(ctx, CGRectMake(0, 0, 100, 100));
    // 4. 渲染
    CGContextStrokePath(ctx);
    // 5. 获取生成的图片
    UIImage * image = UIGraphicsGetImageFromCurrentImageContext();
    // 给当前的图片视图赋值
    self.imageView.image = image ;
    // 将图片保存为二进制数据，将图片写入到本地文件中
    NSData * data = UIImagePNGRepresentation(image);
    [data writeToFile:@"/Users/yyf/Desktop/abc.png" atomically:YES];
```
