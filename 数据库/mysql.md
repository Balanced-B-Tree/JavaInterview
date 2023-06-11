12345678



show create table settle_merchant_opt_log

~~~sql
CREATE TABLE wx_account (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `appid` VARCHAR(30) not null DEFAULT '',
  `secret` VARCHAR(40) not null DEFAULT '',
  `ctime` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `mtime` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
  `is_delete` tinyint(4) NOT NULL DEFAULT '0' COMMENT '是否删除 0否 1是',
  PRIMARY KEY (id),
  KEY `ix_mtime` (`mtime`) USING BTREE,
  KEY `ix_appid` (`appid`) USING BTREE
)ENGINE=InnoDB AUTO_INCREMENT=0 DEFAULT CHARSET=utf8 COMMENT='微信公众号'
~~~

~~~sql
CREATE TABLE `settle_order` (
`id` int(11) unsigned NOT NULL AUTO_INCREMENT COMMENT 'ID',
`order_id` bigint(20) unsigned NOT NULL DEFAULT '0' COMMENT '订单ID',
`shop_id` int(11) unsigned NOT NULL DEFAULT '0' COMMENT '商户ID',
`pro_id` int(11) unsigned NOT NULL DEFAULT '0' COMMENT '项目ID',
`ref_id` bigint(20) unsigned NOT NULL DEFAULT '0' COMMENT '业务方退款ID',
`v_shop_id` int(11) unsigned NOT NULL DEFAULT '0' COMMENT '虚拟店铺ID',
`count` int(11) unsigned NOT NULL DEFAULT '0' COMMENT 'sku总数量',
`refund_id` varchar(32) NOT NULL DEFAULT '' COMMENT '退款ID',
`biz` tinyint(4) unsigned NOT NULL DEFAULT '0' COMMENT '业务方: 1-票务, 2-电商, 3-采购',
`type` tinyint(4) unsigned NOT NULL DEFAULT '0' COMMENT '交易类型: 1-普通订单, 2-拼团订单, 3-退款订单',
`express` int(11) NOT NULL DEFAULT '0' COMMENT '运费',
`verify` tinyint(4) unsigned NOT NULL DEFAULT '0' COMMENT '对账状态: 0-未对账, 1-对账成功, 2-对账失败',
`share` tinyint(4) unsigned NOT NULL DEFAULT '0' COMMENT '分账状态: 0-待处理, 1-处理中, 2-成功, 3-失败, 4-无需处理, 10-线下处理, 20-待确认',
`cash_status` tinyint(4) unsigned NOT NULL DEFAULT '0' COMMENT '提现状态: 0-待处理, 1-处理中, 2-成功, 3-失败, 4-无需处理, 10-线下处理',
`pay_way` varchar(10) NOT NULL DEFAULT '' COMMENT '支付方式',
`goods_money` bigint(20) NOT NULL DEFAULT '0' COMMENT '商品总额',
`share_money` int(11) NOT NULL DEFAULT '0' COMMENT '分账金额',
`account_id` varchar(32) NOT NULL DEFAULT '' COMMENT '分账账户',
`pay_money` bigint(20) NOT NULL DEFAULT '0' COMMENT '实付金额',
`pay_fee` int(11) NOT NULL DEFAULT '0' COMMENT '支付手续费',
`ref_fee` int(11) NOT NULL DEFAULT '0' COMMENT '退款手续费',
`pay_id` varchar(32) NOT NULL DEFAULT '' COMMENT '支付ID',
`pay_time` timestamp NOT NULL DEFAULT '0000-00-00 00:00:00' COMMENT '支付时间',
`entry_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '完成时间',
`ctime` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
`mtime` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
`express_discount` int(11) NOT NULL DEFAULT '0' COMMENT '运费卷折扣',
`merchant_id` int(11) NOT NULL DEFAULT '0' COMMENT '商家平台的商家id',
PRIMARY KEY (`id`),
KEY `ix_ctime` (`ctime`),
KEY `ix_mtime` (`mtime`),
KEY `ix_pro_id_share` (`pro_id`,`share`),
KEY `ix_payid_refid_biz` (`pay_id`,`ref_id`,`biz`),
KEY `ix_order_shop_ref_biz` (`order_id`,`shop_id`,`ref_id`,`biz`),
KEY `ix_merchant_id_biz` (`merchant_id`,`biz`)
) ENGINE=InnoDB AUTO_INCREMENT=799196 DEFAULT CHARSET=utf8 COMMENT='结算订单'
~~~



```
supplierCode

supplier_code
```
