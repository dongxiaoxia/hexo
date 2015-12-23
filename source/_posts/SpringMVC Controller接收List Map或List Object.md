title: SpringMVC Controller����List< Map>��List< Object>
date: 2015-12-23 20:58:44
permalink: spring00001
tags:
- Spring
categories:
- Spring

---
google��һ�����磬��ʱ�ҵ����ֽ���취����Ȼ�����ַ��������Ǻܷ��㣬��ʱ����ô���Űɣ�
##1.ȫ��������װΪһ������
###controller��
```java
/**
 * ���������û�
 *
 * ����ֱ�Ӵ�List  < Map> �������ֻ�����������Ӵ�������һ���ǰ����������ǰ�˱�ΪString������̨�ٽ���������һ�����ǰ����в�����װ��һ������ǰ��JSON.stringify(params)���Ϊ�ַ���������̨����̨���Զ�ת��Ϊ����
 *
 * @param batchCreateVO ��װ�õĶ���
 * @param request
 * @param session
 * @return
 */
@RequestMapping(value = "/batchCreate", produces = MediaTypes.JSON_UTF_8)
@ResponseBody
protected String batchCreate(
        @RequestBody BatchCreateVO batchCreateVO,
        HttpServletRequest request, HttpSession session) {
        //dosomething
	}
```

###��װ�Ķ���
```java
package com.miracle.mby.account.vo;

import java.util.List;
import java.util.Map;

/**
 * �ƶ������������û���װ����
 * <p/>
 * ticket       ���У��ticket
 * mac          ���У��mac
 * refDeptId    ��ҵ��������
 * usersString  �û����������ַ���
 *
 * @author dongxiaoxia
 * @create 2015-12-22 14:33
 */
public class BatchCreateVO {
    private String ticket;
    private String mac;
    private String refDeptId;
    private List<Map> users;

    public String getTicket() {
        return ticket;
    }

    public void setTicket(String ticket) {
        this.ticket = ticket;
    }

    public String getMac() {
        return mac;
    }

    public void setMac(String mac) {
        this.mac = mac;
    }

    public String getRefDeptId() {
        return refDeptId;
    }

    public void setRefDeptId(String refDeptId) {
        this.refDeptId = refDeptId;
    }

    public List<Map> getUsers() {
        return users;
    }

    public void setUsers(List<Map> users) {
        this.users = users;
    }
}
```

###ҳ������
```javascript
var users = [{"userName": "�����û�1","sex":0,"mobile":"15432343213","email":"123@123.com","phone":"123213","departmentIds":[]}];
var params ={
    "ticket":"test",
    "mac":"test",
    "refDeptId":"fa0823254d6011e58434ac220bcd3c54",
    "users":users
};
$.ajax({
    type: 'POST',
    url: 'http://localhost:8081/api/mobile/user/batchCreate',
    data: JSON.stringify(params),
    dataType: 'json', contentType: "application/json; charset=utf-8"
});
```


##2.����ת����Ҫ��List
������List< Map>��List< Object> ����ת��Ϊjson�ַ�����Ȼ�󴫵���̨֮���ٰ��ַ���ת�������





