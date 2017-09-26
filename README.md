# mail



## 阿范德萨发散


##### 合同工和



打撒发送到
===================================



<?php
namespace transfer;
use PHPMailer;
class Mail
{

    //默认从163发往QQ
    protected $host       = "smtp.163.com";
    protected $port       = 25;                     // 设置端口
    protected $username   = '18380335706@163.com';  // 必填，开通SMTP服务的邮箱；任意一个163邮箱均可
    protected $password   = 'woshilvlin123';        // 必填， 以上邮箱对应的密码
    protected $from       = '18380335706@163.com';  // 必填，发件人Email
    protected $fromname   = '服务器';                // 必填，发件人昵称或姓名
    protected $result_mail= '18380335706@163.com';  // 接收回复的邮箱

    public function send($content = '邮件内容', $title = '邮件标题', $to_mail = '591776998@qq.com', $code = "utf-8"){

        $mail= new PHPMailer();
        $mail->CharSet    = $code; 					// 编码格式
        $mail->isSMTP();
        $mail->SMTPAuth   = true;                   // 必填，SMTP服务器是否需要验证，true为需要，false为不需要
        $mail->Host       = $this->host;            // 必填，设置SMTP服务器
        $mail->Port       = $this->port;            // 设置端口
        $mail->Username   = $this->username;  		// 必填，开通SMTP服务的邮箱；任意一个163邮箱均可
        $mail->Password   = $this->password;  	    // 必填， 以上邮箱对应的密码
        $mail->From       = $this->from;    		// 必填，发件人Email
        $mail->FromName   = $this->fromname;        // 必填，发件人昵称或姓名
        $mail->Subject    = $title;       			// 必填，邮件标题（主题）

        //可选，纯文本形势下用户看到的内容
        $text = trim(strip_tags($content));
        if($text){
            $mail->AltBody    = $text;
            $mail->WordWrap   = 50; 				// 自动换行的字数
        }

        $mail->msgHTML($content);
        $mail->addReplyTo($this->result_mail);		// 收件人回复的邮箱地址
        $mail->addAddress($to_mail); 				// 收件人邮箱
        $mail->isHTML(true); 						// 是否以HTML形式发送，如果不是，请删除此行
        if($mail->send()){
            return true;
        }else{
            return false;
        }
    }

}





