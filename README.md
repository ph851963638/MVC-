# MVC-

ModelAndView  视图及数据
创建  

ModelAndView mav=new ModelAndView()   无参构造方法 对象
if（resut）{
mav.setviewname("名称");  //跳转页面//web-inf/jsp
}else{



//session.setAttribute("msg","登录信息有误")；
 mav.addObject("msg",登陆信息有误);
//return "redirect:/index.jsp;// web-inf/index;
 mav.setViewName("redirect:/index.jsp");
 


}

