# 异步校验

----

<link rel="stylesheet" type="text/css" href="bootstrap.css" media="all" />


<form class="form-horizontal" id="form-login">
  <div class="control-group">
    <label class="control-label" for="inputEmail">Email</label>
    <div class="controls">
      <input type="text" name="username" id="inputEmail"
        placeholder="Email"
        required />
      <span class="help-inline"><strong>*</strong> 必填，请输入您的邮箱账号。</span>
    </div>
  </div>
  <div class="control-group">
    <label class="control-label" for="inputPassword">Password</label>
    <div class="controls">
      <input type="password" name="password" id="inputPassword"
        placeholder="Password"
        required minlength="6" maxlength="20" />
      <span class="help-inline"><strong>*</strong> 必填，请输入您的密码。</span>
    </div>
  </div>
  <div class="control-group">
    <div class="controls">
      <label class="checkbox">
        <input type="checkbox"> Remember me
      </label>
      <button type="submit" class="btn">Sign in</button>
    </div>
  </div>
</form>


<script type="text/javascript">
seajs.use(['$', 'webforms', 'validator'], function($, WebForms, Validator){
    var form = document.getElementById("form-login");
    var loginForm = new Validator(form, {
        trigger: "blur,keyup",
        fastbreak: true,
        rules: {
            "username": function(value, elem, RULES){
                return RULES.email.test(value) || RULES.mobile.test(value);
            }
        },
        onerror: {
            "*": function(elem){
                $(elem).parent().parent().addClass("error");
            }
        },
        onpass: {
            "*": function(elem){
                $(elem).parent().parent().removeClass("error");
            }
        }
    });
});
</script>
