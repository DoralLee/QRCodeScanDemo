# QRCodeScanDemo

`本项目用于二维码扫描`

1. 如何使用

	首先引入头文件
	
	```
	#import "LKQRCodeViewController.h"
	```
	
	在相应事件中如下操作
	
	```
	- (IBAction)scanButtonClick:(UIButton *)sender {
	LKQRCodeViewController *qrCodeVC = [[LKQRCodeViewController alloc] init];
	   qrCodeVC.LKQRCodeSuccessBlock = ^(LKQRCodeViewController *aqrvc, NSString *qrString) {
	       self.scanContentLabel.text = qrString;
	       [aqrvc dismissViewControllerAnimated:NO completion:nil];
	   };
	   qrCodeVC.LKQRCodeFailBlock = ^(LKQRCodeViewController *aqrvc){
	       self.scanContentLabel.text = @"fail~";
	       [aqrvc dismissViewControllerAnimated:NO completion:nil];
	   };
	   qrCodeVC.LKQRCodeCancleBlock = ^(LKQRCodeViewController *aqrvc){
	       [aqrvc dismissViewControllerAnimated:NO completion:nil];
	       self.scanContentLabel.text = @"cancle~";
	   };
	   [self presentViewController:qrCodeVC animated:YES completion:nil];
	}
	```
	其中LKQRCodeSuccessBlock是扫描成功的回调，LKQRCodeFailBlock是失败的时候回调，LKQRCodeCancleBlock取消扫描回调
	
	> 相关的扫描设置在LKQRCodeViewController.m文件中
