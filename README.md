邮件发送的封装
=================================

## 1.环境
php>=5
openssl扩展
sokets扩展
thinkphp5.*

## 2.依赖
                composer require "phpmailer/phpmailer:5.0"
                
## 3.使用

                
                $to_mail        = '591776998@qq.com';		//接收者的邮箱
                $title          = 'test_transfer';			//标题
                $content        = 'success!';				//内容 支持html格式
                $mail = new \transfer\Mail();
                $res = $mail->send($content, $title,$to_mail);


