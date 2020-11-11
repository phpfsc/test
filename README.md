<?php
error_reporting(1);
require_once("configExternal.php");
?>
<html>
   <head>
      <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
   <link rel="stylesheet" href="css/registration.css">
     <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap" rel="stylesheet">
   </head>
   <body>
       <div class="login-heading">
            <h3>Register As New Author</h3>
         </div>
       <div class="container">
      <div class="krna col-md-12 col-lg-12 col-sm-12 col-xs-12">
         
         <div class="register">
             <div class="personalform">
            <div class="headings col-md-12 col-lg-12 col-sm-12 col-xs-12">
               <h3>Login Details</h3>
            </div>
            <form class="registration" id="registration" method="post"  enctype="multipart/form-data">
             <input type="hidden" id="fCityUrl" value="<?=base64_encode(base64_encode('fetch_city.php'))?>">  
			 <input type="hidden" id="fUrl" value="<?=base64_encode(base64_encode('fetch_state.php'))?>">  
			 <input type="hidden" id="SaveDetails" value="<?=base64_encode(base64_encode('saveRegisterData.php'))?>">  
			   <!-- username  -->
			   <input type="hidden" id="txtUserType" name="txtUserType" value="3">
               <div class="col-md-12">
               <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                  <label class="las">Username :<strong style="color: white">*</strong></label>
                  <div class="puright">
                     <input type="text" class="form-control" name="username" id="username" autocomplete="off" placeholder="Username" onkeypress="return AvoidSpace(event)"  oninput="return CheckUserName(this.value);" maxlength="50">
                      <span class="text-danger"></span>
					 <input type="hidden" id="existing_status_username">
					
                     <span id="username-availability-status" class="text-danger"></span>
                     <span id="username-err-msg" class="text-danger"></span>
                  </div>
               </div>
               <!-- username -->
               <!-- password  -->
               <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                  <label class="las">Password :<strong style="color: white">*</strong></label>
                  <div class="puright">
                     <input type="password" class="form-control" placeholder="Password" autocomplete="off" id="password" name="password"  maxlength="25">
                      <span class="text-danger"></span>
					 <span id="pass-err-msg" class="text-danger"></span>
                     <span id="pass-err-format" class="text-danger" style="font-size: 10px;"></span>
                  </div>
               </div>
               <!-- password end  -->
               <!-- confirm password  -->
               <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                  <label class="las">Confirm Password :<strong style="color:white">*</strong></label>
                  <div class="puright">
                     <input type="password" class="form-control" placeholder="Confirm Password" autocomplete="off" name="cnf_password" id="cnf_password"  maxlength="25">
                      <span class="text-danger"></span>
					 <span id="cnf-pass-err-msg" class="text-danger">
                     </span>
                  </div>
               </div>
               <!-- end confirm password  -->
               <!-- email -->
               <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                  <label class="las">Email:<strong style="color: white">*</strong></label>
                  <div class="puright">
                     <input type="text" class="form-control" placeholder="Email" onblur="CheckEmail(this.value)" onkeypress="return AvoidSpace(event)" autocomplete="off" name="email" id="email" maxlength="50">
                      <span class="text-danger"></span>
					 <!-- <span id="email-availability-status"></span> -->
                     <input type="hidden" id="existing_status_email">
                     <span id="email-err-msg" class="text-danger"></span>
                  </div>
               </div>
               <!-- end email -->
               </div>
               </div>
                <div class="personalform">
               <div class="headings col-md-12 col-lg-12 col-sm-12 col-xs-12">
                  <h3> Personal Details</h3>
               </div>
               <div class="col-md-12">
                  <!-- author title -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las"> Title: </label>
                     <div class="puright">
                        <select name="title" class="form-control" id="title" style="display: inline-block;height: 18px;margin: 0 0 0;color: #888;-moz-border-radius: 5px;-webkit-border-radius: 5px;
                           border-radius: 0 !important;
                           box-sizing: content-box;
                           outline: none;
                           padding: 6px 4px !important;">
                           <option value="">Select Title</option>
						   <?php
						   $query=mysqli_query($conn,"select * from salutation_master");
						   while($row=mysqli_fetch_array($query))
						   {
							 echo '<option value="'.$row[salutationName].'">'.$row[salutationName].'</option>' ;
						   }
                           ?>
                        </select>
                        <span class="text-danger"></span>
					   <!-- other title input box -->
                        <br>
                        <input class="form-control" maxlength="15" placeholder="title" type="text" id="title_other" name="title_other" data-error="Title is requiwhite" style=" display: none; ">
                        <!-- other title input box -->
                        <span id="title-err-msg" class="text-danger"></span>
                     </div>
                  </div>
                  <!-- title -->
                  <!-- end author title -->
                  <!-- first name -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las"> First Name:<strong style="color: white">*</strong></label>
                     <div class="puright">
                        <input type="text" class="form-control" name="fname" id="fname" autocomplete="off" placeholder="First Name" onkeypress="return AvoidSpace(event)" maxlength="50">
                         <span class="text-danger"></span>
						<span id="first-name-err-msg" class="text-danger"></span>
                     </div>
                  </div>
                  <!-- first name -->
                  <!-- middle name -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las">Middle name:</label>
                     <div class="puright">
                        <input type="text" class="form-control" placeholder="Middle name" autocomplete="off"  name="middle_name" onkeypress="return AvoidSpace(event)" id="middle_name" maxlength="50">
                         <span class="text-danger"></span>
						<span id="middle-name-err-msg" class="text-danger"></span>
                     </div>
                  </div>
                  <!-- end middle name -->
                  <!-- last name  -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las">
                     Last Name:<strong style="color: white">*</strong>
                     </label>
                     <div class="puright">
                        <input type="text" class="form-control" placeholder="Last Name" autocomplete="off" name="l_name" id="l_name" onkeypress="return AvoidSpace(event)"  maxlength="50">
                         <span class="text-danger"></span>
						<span id="last-name-err-msg" class="text-danger"></span>
                     </div>
                  </div>
                  <!-- end last name  -->
               </div>
               <div class="col-md-12">
                  <!-- degree  -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las">
                     Degree:<strong style="color: white">*</strong>
                     </label>
                     <div class="puright">
                        <input type="text" class="form-control" placeholder="Degree" autocomplete="off" onkeypress="return AvoidChars(event)"  name="degree" id="degree" maxlength="100">
                         <span class="text-danger"></span>
						<span id="degree-err-msg" class="text-danger"></span>
                     </div>
                  </div>
                  <!-- end row -->
                  <!-- designation -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las">
                     Designation:<strong style="color: white">*</strong>
                     </label>
                     <div class="puright">
                        <input type="text" class="form-control" placeholder="Designation" onkeypress="return AvoidChars(event)" autocomplete="off"  name="designation" id="designation" maxlength="100">
                         <span class="text-danger"></span>
						<span id="designation-err-msg" class="text-danger"></span>
                     </div>
                  </div>
                  <!-- end designation -->
                  <!-- speciality -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las"> Speciality:<strong style="color: white">*</strong></label>
                     <div class="puright">
                        <select class="form-control" name="speciality" id="speciality" style="display: inline-block; height: 18px; margin: 0 0 0;color: #888; -moz-border-radius: 5px; -webkit-border-radius: 5px; border-radius: 0 !important; box-sizing: content-box; outline: none; padding: 6px 4px !important;">
                           <option value="">-----Select Speciality-----</option>
                          <?php
						  $query3= mysqli_query($conn,"select * from speciality_master");
						  while($row3=mysqli_fetch_array($query3))
						  {
							  echo '<option value="'.base64_encode(base64_encode($row3[specialityId])).'">'.$row3[specialityName].'</option>';
						  }
						  ?>
                        </select>
                         <span class="text-danger"></span>
						<!--<input type="text" class="form-control" placeholder="Speciality" autocomplete="off" onkeyup="CheckFirstChar(event.keyCode, this);" onkeydown="return CheckFirstChar(event.keyCode, this);" name="speciality" id="speciality" value="">-->
                        <span id="speciality-err-msg" class="text-danger"></span>
                     </div>
                  </div>
                  <!-- end specialty -->
               </div>
               </div>
                <div class="personalform">
               <div class="headings col-md-12 col-lg-12 col-sm-12 col-xs-12">
                  <h3>Primary Address</h3>
               </div>
               <div class="col-md-12">
                  <!-- institution -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las">
                     Institution:<strong style="color: white">*</strong>
                     </label>
                     <div class="puright">
                        <input type="text" class="form-control" autocomplete="off" placeholder="Institution" name="institution" id="institution" onkeypress="return AvoidChars(event)"  maxlength="100">
                         <span class="text-danger"></span>
						<span id="institution-err-msg" class="text-danger"></span>
                     </div>
                  </div>
                  <!-- end of institutioin -->
                  <!-- department  -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las">
                     Department:<strong style="color: white">*</strong>
                     </label>
                     <div class="puright">
                        <input type="text" class="form-control" placeholder="Department"  onkeypress="return AvoidChars(event)" autocomplete="off" name="dept" id="dept" maxlength="100">
                         <span class="text-danger"></span>
						<span id="department-err-msg" class="text-danger"></span>
                     </div>
                  </div>
                  <!-- department -->
                  <!-- country -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las">
                     Country:<strong style="color: white">*</strong>
                     </label>
                     <div class="puright">
                        <select class="form-control" onchange="FetchState(this.value)" name="country" id="country" style="display: inline-block; height: 18px; margin: 0 0 0;color: #888; -moz-border-radius: 5px; -webkit-border-radius: 5px; border-radius: 0 !important; box-sizing: content-box; outline: none; padding: 6px 4px !important;">
                           <option value="">-----Select Country-----</option>
                           <?php
						   $query2=mysqli_query($conn,"select * from country_master");
						   while($row2=mysqli_fetch_array($query2))
						   {
							   echo '<option value="'.base64_encode(base64_encode($row2[countryId])).'">'.$row2[countryName].'</option>';
						   }
						   ?>
                        </select>
                         <span class="text-danger"></span>
						<span id="country-err-msg" class="error"></span>
                     </div>
                  </div>
                  <!-- end country -->
                  <!-- state -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las">State/Province:<strong style="color: white">*</strong></label>
                     <div class="puright">
					 <select class="form-control" name="state" id="state" onchange="FetchCity(this.value)" style="display: inline-block; height: 18px; margin: 0 0 0;color: #888; -moz-border-radius: 5px; -webkit-border-radius: 5px; border-radius: 0 !important; box-sizing: content-box; outline: none; padding: 6px 4px !important;">
                           <option value="">-----Select State-----</option>
                           
                        </select>
                       
                         <span class="text-danger"></span>
						<span id="state-err-msg" class="text-danger"></span>
                     </div>
                  </div>
                  <!-- end state -->
               </div>
               <div class="col-md-12">
                  <!-- city section starts over here -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las"> City:<strong style="color: white">*</strong></label>
                     <div class="puright">
					 <select class="form-control" name="city" id="city"  style="display: inline-block; height: 18px; margin: 0 0 0;color: #888; -moz-border-radius: 5px; -webkit-border-radius: 5px; border-radius: 0 !important; box-sizing: content-box; outline: none; padding: 6px 4px !important;">
                           <option value="">-----Select City-----</option>
                           
                      </select>
                        
                         <span class="text-danger"></span>
						<span id="city-err-msg" class="text-danger"></span>
                     </div>
                  </div>
                  <!-- city section ends over here  -->
                  <!-- address -->
                  <div class="col-md-6 col-lg-6 col-sm-12 col-xs-12">
                     <label class="las">
                     Address:<strong style="color: white">*</strong>
                     </label>
                     <div class="puright">
                        <textarea  autocomplete="off"  class="form-control" onkeypress="return AvoidChars(event)" placeholder="Address" name="address" id="address" maxlength="255"></textarea>
                         <span class="text-danger"></span>
						<span id="address-err-msg" class="text-danger"></span>
                     </div>
                  </div>
                  <!-- address -->
                  <!-- pincod  -->
                  <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las">
                     Pin Code:<strong style="color: white">*</strong>
                     </label>
                     <div class="puright">
                        <input type="text" id="pincode" class="form-control quantity" autocomplete="off" onkeypress="return AvoidChars(event)" placeholder="PIN Code" maxlength="10" name="pincode" ondrop="return false;" value="">
                         <span class="text-danger"></span>
						<span id="errors" style="color: white; display: none">* Only Input Digit and PIN Code</span>
                     </div>
                     <span id="pincode-err-msg" class="text-danger"></span>
                  </div>
                  <!-- end pincode -->
                  <!-- phone -->
				  
                  
                  <!-- end of phone -->
               </div>
			   <div class="col-md-12">
			   <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las">Country Code: <strong style="color: white">*</strong></label>
                     <div class="puright">
                        <select id="txtCountryCode" class="form-control" name="txtCountryCode">
							 <option value="">-----------Country Code----------</option>
							 <?php
							  $queryCode=mysqli_query($conn,"select * from country_code_master");
							  while($rowCode=mysqli_fetch_array($queryCode))
							  {
							 ?>
							 <option value="<?=$rowCode['countryCode']?>"><?=$rowCode['countryCode']?></option>
							 
							 <?php
							  }
							 ?>
				        </select>
                         <span class="text-danger"></span>
						<span id="error" style="color: white; display: none">* Only Input Mobile and Phone No.</span>
                        <span id="phone-err-msg" class="text-danger"></span>
                     </div>
                  </div>
			   <div class="col-md-3 col-lg-3 col-sm-12 col-xs-12">
                     <label class="las">Phone: <strong style="color: white">*</strong></label>
                     <div class="puright">
                        <input type="text" id="phone" class="form-control" placeholder="Phone" onkeypress="return AvoidChars(event)" autocomplete="off" name="phone" maxlength="12">
                         <span class="text-danger"></span>
						<span id="error" style="color: white; display: none">* Only Input Mobile and Phone No.</span>
                        <span id="phone-err-msg" class="text-danger"></span>
                     </div>
                  </div>
               <!-- author cv -->
               <div class="col-md-6 col-lg-6 col-sm-12 col-xs-12">
                  <label class="las">
                  Upload CV:
                  </label>
                  <div class="puright">
                     <input type="file" class="form-control" name="auth_signature" id="auth_signature" accept="application/vnd.openxmlformats-officedocument.wordprocessingml.document" style="border: 0px solid white; height:auto;padding: 0 0 0 0;" value=""/>
                      <br><br><small style="color:white">(Only doc,docx,pdf file formats)</small>
                      <br><small style="color:white">Upload your Resume/CV. Please do not Upload your manuscript here. Once you Complete your Registration. Please visit to Author Dashboard to submit manuscript.</small>
					  <span class="text-danger"></span>
					 <input type="hidden" name="file_upload_status" id="file_upload_status">
                     <span id="cv-err-msg" class="text-danger"></span> <br>
                    
                  </div>
               </div>
               </div>
               <input type="hidden" name="image" value="admin.jpg">
               <div class="puright col-md-12 col-lg-12 col-sm-12 col-xs-12">
                   <div class="purightbutton">
                  <button type="button" class="btn btn-primary" id="readmore" onclick="VerifyDetails()">Submit</button>
               </div>
               </div>
               </div>
            </form>
         </div>
      </div>
      </div>
      
         <div class="modal fade" id="otpmodal" tabindex="-1" role="dialog" aria-labelledby="otpmodal" aria-hidden="true" style="display:none;">
           <div class="modal-dialog modal-dialog-centewhite" role="document">
             <div class="modal-content">
            <div class="modal-header otptitle">
                <h5 class="modal-title">OTP Verification</h5>
                
            </div>
            <div class="modal-body">
                <form id="otp_save_data" class="myform-control" method="POST" action="" name="save_data" onsubmit="return false;" role="form">
                    <div class="row">
                        <div class="col-md-12">
                            <label>Please enter your one time password.</label>
                        </div>
                        <div class="col-md-12">
                            <input type="hidden" name="otp_value" id="otp_value" value=""><input type="hidden" name="SNo" id="SNo" value="">
                            <input type="text" name="otp" id="otp" placeholder="Please enter otp.." class="myform-control" maxlength="4">
                            <p class="text-danger" style="color:red;text-align:center"></p>
						</div>
                    </div>
                    <div class="row">
                        <div class="col-md-12 pull-right">
						    <button type="button" class="btn btn-info" id="otp_Verify" onclick="verify_otp();">Verify OTP</button>
                            <button type="button"  class="btn btn-info" id="resend_otp" onclick="resend();">Resend OTP</button>
                            
                          
                        </div>
                    </div>
                </form>
            </div>
            
        </div>
    </div>
</div> 
</body>
<script>
function resend()
{
  $("#resend_otp").prop('disabled',true);
	           $.ajax({
					url:atob(atob('<?=base64_encode(base64_encode("otpResend.php"))?>')), 
                    type: 'POST',
                    data: {"email":$("#email").val(),"username":$("#username").val(),"txtUserType":$("#txtUserType").val()},
                   
                    success: function (result) {
						
                          var data = JSON.parse(result);
                          if (data.error) {
							$("#resend_otp").prop('disabled',false);
							$('#otp').next('p').html(data.error_msg);
                            
                        }
						else
						{
                          $('#otp').next('p').html(data.error_msg);
							
						}
                       
                    },
                    error: function (jqXHR, status, err) {
						if(jqXHR.status=='404')
						{
							
							$("#resend_otp").prop('disabled',false);
						}
						if(jqXHR.status=='500')
						{
							
							$("#resend_otp").prop('disabled',false);
						}
						
                        
                    },
                    complete: function (jqXHR, status) {
                      $("#resend_otp").prop('disabled',false);  
                    }
                });
	   	
}
</script>
<script>
function verify_otp()
{
	var errmsg="";
	var validata=true;
	var focusid="";
	$("#otp_Verify").prop("disabled",true);
	if($("#otp").val()==='')
	{
		validata=false;
		focusid="otp";
		if(errmsg=='')
		{
			errmsg="Please Enter Otp";
		}
		else
		{
			errmsg="<br>Please Enter Otp";
		}
	}
	else if(isNaN($("#otp").val()) || $("#otp").val().length!=4)
	{
		validata=false;
		focusid="otp";
		if(errmsg=='')
		{
			errmsg="Invalid Otp";
		}
		else
		{
			errmsg="<br>Invalid Otp";
		}
	}
	if(validata==false)
	{
		$('#'+focusid).next('p').html(errmsg);
		$("#otp_Verify").prop("disabled",false);
	}
	else
	{
		       $('#otp').next('p').html('');
               $.ajax({
					url:atob(atob('<?=base64_encode(base64_encode("verifyOtp.php"))?>')), 
                    type: 'POST',
                    data: {"otp":$("#otp").val()},
                    
                    success: function (result) {
						  var data=JSON.parse(result);
						  if(data.error)
						  {
							 $('#otp').next('p').html(data.error_msg);
							 $("#otp_Verify").prop("disabled",false);
						  }
						  else
						  {
							$('#otp').next('p').html("Please Wait");
							$("#otp_Verify").prop("disabled",false);
                            registerStep2();
							
							
						  }
                       
                    },
                    error: function (jqXHR, status, err) {
						if(jqXHR.status=='404')
						{
							
							$("#otp_Verify").prop("disabled",false);
						}
						if(jqXHR.status=='500')
						{
							
							$("#otp_Verify").prop("disabled",false);
						}
						
                        
                    },
                    complete: function (jqXHR, status) {
                        $("#otp_Verify").prop("disabled",false);
                    }
                });
		
	}
}
</script>
<script>
function registerStep2()
{
	            $("#otp_Verify").attr("disabled",true);
		        var formData = new FormData();
        		var other_data = $('#registration').serializeArray();
				
        		$.each(other_data,function(key,input){
        			formData.append(input.name,input.value);
        		});
				
					
					formData.append("auth_signature",$("#auth_signature")[0].files[0]);
				
				$.ajax({
					url:atob(atob('<?=base64_encode(base64_encode("saveRegisterData.php"))?>')), 
                    type: 'POST',
                    data: formData,
                    async: true,
                    cache: false,
                    contentType: false,
                    processData: false,
                    success: function (result) {
						//alert(result);
                          var data = JSON.parse(result);
                          if (data.error) {
							$("#readmore").prop('disabled',false);
							$('#'+data.focusid).next('p').html(errmsg);
                            $('#'+data.focusid).focus();
							$("#otp_Verify").attr("disabled",false);
                        }
						else
						{
							  $('#otpmodal').find('.modal-body').html('<p style="text-align:center"><span style="color:green">'+data.error_msg+'</span></p><p style="text-align:center"><a href="login.php"><button class="btn btn-primary login">Login</button></a></p>');
							  $("#registration")[0].reset();
							  $("#otp_Verify").attr("disabled",false);
							
							
						}
                       
                    },
                    error: function (jqXHR, status, err) {
						if(jqXHR.status=='404')
						{
							
							$("#otp_Verify").attr("disabled",false);
						}
						if(jqXHR.status=='500')
						{
							
							$("#otp_Verify").attr("disabled",false);
						}
						
                        
                    },
                    complete: function (jqXHR, status) {
                      $("#otp_Verify").attr("disabled",false);
                    }
                });
	   
}
</script>
  <script>
  function validateEmail(field) {
    var regex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,5}$/;
    return (regex.test(field)) ? true : false;
}
  </script>
   <script>
   function VerifyDetails()
   {
	  $("#readmore").prop('disabled',true);
	   var validata=true;
	   var focusid="";
	   var errmsg="";
	   if($("#username").val()==='')
	   {
		   validata=false;
		   focusid="username";
		   if(errmsg==='')
		   {
			   errmsg="Please Enter UserName";
		   }
		   else
		   {
			   errmsg="<br>Please Enter UserName";
		   }
	   }
	   
	   else if($("#password").val()==='')
	   {
		   validata=false;
		   focusid="password";
		   if(errmsg==='')
		   {
			   errmsg="Please Enter Password";
		   }
		   else
		   {
			   errmsg="<br>Please Enter Password";
		   }
	   }
	   else if($("#cnf_password").val()==='')
	   {
		   validata=false;
		   focusid="cnf_password";
		   if(errmsg==='')
		   {
			   errmsg="Please Re-Enter Password";
		   }
		   else
		   {
			   errmsg="<br>Please Re-Enter Password";
		   }
	   }
	   else if($("#cnf_password").val()!==$("#password").val())
	   {
		   validata=false;
		   focusid="cnf_password";
		   if(errmsg==='')
		   {
			   errmsg="Password Mis-Match";
		   }
		   else
		   {
			   errmsg="<br>Password Mis-Match";
		   }
	   }
	   else if($("#email").val()==='')
	   {
		   validata=false;
		   focusid="email";
		   if(errmsg==='')
		   {
			   errmsg="Please Enter Email";
		   }
		   else
		   {
			   errmsg="<br>Please Enter Email";
		   }
	   } 
	   else if(!validateEmail($("#email").val()))
	   {
		   validata=false;
		   focusid="email";
		   if(errmsg==='')
		   {
			   errmsg="Invalid Email";
		   }
		   else
		   {
			   errmsg="<br>Invalid Email";
		   }
	   } 
	   else if($("#title").val()==='')
	   {
		   validata=false;
		   focusid="title";
		   if(errmsg==='')
		   {
			   errmsg="Please Choose Title";
		   }
		   else
		   {
			   errmsg="<br>Please Choose Title";
		   }
	   } 
	   else if($("#fname").val()==='')
	   {
		   validata=false;
		   focusid="fname";
		   if(errmsg==='')
		   {
			   errmsg="Please Enter First Name";
		   }
		   else
		   {
			   errmsg="<br>Please Enter First Name";
		   }
	   }
	   // else if($("#middle_name").val()==='')
	   // {
		   // validata=false;
		   // focusid="middle_name";
		   // if(errmsg==='')
		   // {
			   // errmsg="Please Enter Middle Name";
		   // }
		   // else
		   // {
			   // errmsg="<br>Please Enter First Name";
		   // }
	   // }
	   else if($("#l_name").val()==='')
	   {
		   validata=false;
		   focusid="l_name";
		   if(errmsg==='')
		   {
			   errmsg="Please Enter Last Name";
		   }
		   else
		   {
			   errmsg="<br>Please Enter Last Name";
		   }
	   }
	   else if($("#degree").val()==='')
	   {
		   validata=false;
		   focusid="degree";
		   if(errmsg==='')
		   {
			   errmsg="Please Enter Degree Name";
		   }
		   else
		   {
			   errmsg="<br>Please Enter Degree Name";
		   }
	   }
	   else if($("#designation").val()==='')
	   {
		   validata=false;
		   focusid="designation";
		   if(errmsg==='')
		   {
			   errmsg="Please Choose Designation";
		   }
		   else
		   {
			   errmsg="<br>Please Choose Designation";
		   }
	   }
	   else if($("#speciality").val()==='')
	   {
		   validata=false;
		   focusid="speciality";
		   if(errmsg==='')
		   {
			   errmsg="Please Choose Speciality";
		   }
		   else
		   {
			   errmsg="<br>Please Choose Speciality";
		   }
	   }
	   else if($("#institution").val()==='')
	   {
		   validata=false;
		   focusid="institution";
		   if(errmsg==='')
		   {
			   errmsg="Please Enter Institution Name";
		   }
		   else
		   {
			   errmsg="<br>Please Enter Institution Name";
		   }
	   }
	   else if($("#dept").val()==='')
	   {
		   validata=false;
		   focusid="dept";
		   if(errmsg==='')
		   {
			   errmsg="Please Enter Department Name";
		   }
		   else
		   {
			   errmsg="<br>Please Enter Department Name";
		   }
	   }
	   else if($("#country").val()==='')
	   {
		   validata=false;
		   focusid="country";
		   if(errmsg==='')
		   {
			   errmsg="Please Choose Country";
		   }
		   else
		   {
			   errmsg="<br>Please Choose Country";
		   }
	   }
	   else if($("#state").val()==='')
	   {
		   validata=false;
		   focusid="state";
		   if(errmsg==='')
		   {
			   errmsg="Please Choose state";
		   }
		   else
		   {
			   errmsg="<br>Please Choose state";
		   }
	   }
	   else if($("#city").val()==='')
	   {
		   validata=false;
		   focusid="city";
		   if(errmsg==='')
		   {
			   errmsg="Please Choose city";
		   }
		   else
		   {
			   errmsg="<br>Please Choose city";
		   }
	   } 
	   else if($("#address").val()==='')
	   {
		   validata=false;
		   focusid="address";
		   if(errmsg==='')
		   {
			   errmsg="Please Enter address";
		   }
		   else
		   {
			   errmsg="<br>Please Enter address";
		   }
	   } 
	   else if($("#address").val()==='')
	   {
		   validata=false;
		   focusid="address";
		   if(errmsg==='')
		   {
			   errmsg="Please Enter address";
		   }
		   else
		   {
			   errmsg="<br>Please Enter address";
		   }
	   }
	   else if($("#pincode").val()==='')
	   {
		   validata=false;
		   focusid="pincode";
		   if(errmsg==='')
		   {
			   errmsg="Please Enter pincode";
		   }
		   else
		   {
			   errmsg="<br>Please Enter pincode";
		   }
	   }
	   else if(isNaN($("#pincode").val()) && $("#txtCountryCode").val()=='+91')
	   {
		   validata=false;
		   focusid="pincode";
		   if(errmsg==='')
		   {
			   errmsg="Invalid pincode";
		   }
		   else
		   {
			   errmsg="<br>Invalid pincode";
		   }
	   }
	   else if($("#txtCountryCode").val()==='')
	   {
		   validata=false;
		   focusid="txtCountryCode";
		   if(errmsg==='')
		   {
			   errmsg="Please Choose Country Code";
		   }
		   else
		   { 
			   errmsg="<br>Please Choose Country Code";
		   }
	   }
	   else if($("#txtCountryCode").val()=='+91' && (isNaN($("#pincode").val()) || $("#pincode").val().length!='6'))
	{
		validata=false;
		focusid="pincode";
		if(errmsg=='')
		{
			errmsg="Invalid Pincode";
		}
		else
		{
			errmsg="<br>Invalid Pincode";
		}
	}
	else if($("#txtCountryCode").val()!='+91' && $("#pincode").val().length<4)
	{
		validata=false;
		focusid="pincode";
		if(errmsg=='')
		{
			errmsg="Invaid PinCode";
		}
		else
		{
			errmsg="<br>Invaid PinCode";
		}
	}
	
	   else if($("#phone").val()==='')
	   {
		   validata=false;
		   focusid="phone";
		   if(errmsg==='')
		   {
			   errmsg="Please Enter Mobile/Phone No";
		   }
		   else
		   {
			   errmsg="<br>Please Enter Mobile/Phone No";
		   }
	   }
	   else if(!validateMobile($("#phone").val()) && $("#txtCountryCode").val()=='+91')
	{
		validata=false;
		focusid="phone";
		if(errmsg=='')
		{
			errmsg="Please Enter Valid Mobile No";
		}
		else
		{
			errmsg="<br>Please Enter Valid Mobile No";
		}
	}
	else if($("#txtCountryCode").val()!='+91' && (isNaN($("#phone").val()) || $("#phone").val().length<8))
	{
		validata=false;
		focusid="phone";
		if(errmsg=='')
		{
			errmsg="Please Enter Valid Mobile No";
		}
		else
		{
			errmsg="<br>Please Enter Valid Mobile No";
		}
	}
	    
	   if(validata==false)
	   {
		   $("span").html('');
		   $('#'+focusid).next('span').html(errmsg);
		   $("#"+focusid).focus();
		   $("#readmore").prop('disabled',false);
	   }
	   else
	   {
		        var formData = new FormData();
        		var other_data = $('#registration').serializeArray();
				
        		$.each(other_data,function(key,input){
        			formData.append(input.name,input.value);
        		});
				
					
					formData.append("auth_signature",$("#auth_signature")[0].files[0]);
				
				$.ajax({
					url:atob(atob('<?=base64_encode(base64_encode("resgistrationStep1.php"))?>')), 
                    type: 'POST',
                    data: formData,
                    async: true,
                    cache: false,
                    contentType: false,
                    processData: false,
                    success: function (result) {
						// alert(result);
                          var data = JSON.parse(result);
                          if (data.error) {
							$("#readmore").prop('disabled',false);
							 $('#'+data.focusid).next('span').html(data.error_msg);
                            $('#'+data.focusid).focus();
                        }
						else
						{
							  $("#otpmodal").modal({
									backdrop: 'static',
									keyboard: false
								});
							
							
						}
                       
                    },
                    error: function (jqXHR, status, err) {
						if(jqXHR.status=='404')
						{
							
							$("#readmore").prop('disabled',false);
						}
						if(jqXHR.status=='500')
						{
							
							$("#readmore").prop('disabled',false);
						}
						
                        
                    },
                    complete: function (jqXHR, status) {
                      $("#readmore").prop('disabled',false);  
                    }
                });
	   }
   }
   </script>
   <script>
    function CheckUserName(val)
	{
		            if(val!=='')
                    {
						$("#readmore").prop('disabled', true);
	                
					$.ajax({
					url:'checkUserName.php', 
                    type: 'POST',
                    data: {"txtUserName":val},
                    
                    success: function (result) {
						
                         
                           var data=JSON.parse(result);
						   if(data.error)
						   {
							   $('#username').next('span').html(data.error_msg);
							   $('#username').focus();
							   $("#username-availability-status").html('');
							   $("#readmore").prop('disabled',true);
						   }
						   else
						   {
							   $('#username').next('span').html('');
							   $("#username-availability-status").html(data.error_msg);
						       $("#readmore").prop('disabled',false);
						   }
                       
                    },
                    error: function (jqXHR, status, err) {
						if(jqXHR.status=='404')
						{
							toastr.error("Page Not Found");
							$("#readmore").prop('disabled',false);
						}
						if(jqXHR.status=='500')
						{
							toastr.error("Internal Server Error");
							$("#readmore").prop('disabled',false);
						}
						
                        
                    },
                    complete: function (jqXHR, status) {
                     $("#readmore").prop('disabled',false);
                    }
                 });
					}
					else
					{
						$('#username').next('span').html('');
						
						$("#readmore").prop('disabled', false);
					}
	                
	
	
	 
	 
 


	}
   </script>
   <script>
    function CheckEmail(val)
	{
		            if(val!=='')
                    {
						$("#readmore").prop('disabled', true);
	                
					$.ajax({
					url:'checkEmail.php', 
                    type: 'POST',
                    data: {"txtEmail":val,"txtUserType":$("#txtUserType").val()},
                    
                    success: function (result) {
						
                           
                           var data=JSON.parse(result);
						   if(data.error)
						   {
							    $('#email').next('span').html(data.error_msg);
							    $("#email").focus();
							    $("#readmore").prop('disabled',true);
							  
						   }
						   else
						   {
							   $('#email').next('span').html('');
						       $("#readmore").prop('disabled',false);
						   }
                       
                    },
                    error: function (jqXHR, status, err) {
						if(jqXHR.status=='404')
						{
							toastr.error("Page Not Found");
							$("#readmore").prop('disabled',false);
						}
						if(jqXHR.status=='500')
						{
							toastr.error("Internal Server Error");
							$("#readmore").prop('disabled',false);
						}
						
                        
                    },
                    complete: function (jqXHR, status) {
                     $("#readmore").prop('disabled',false);
                    }
                 });
					}
					else
					{
						$('#email').next('span').html('');
						$("#readmore").prop('disabled', false);
					}
	                
	
	
	 
	 
 


	}
   </script>
   <script>
   function validateMobile(mobile) {
	  if(isNaN(mobile))
	  {
		  return false;
	  }
	  else if(mobile.length!=10)
	  {
		  return false;
	  }
	  
	  else
	  {
		  return true;
	  }
     }
   </script>
   <script>
function FetchState(Id)
{
	var validata=true;
	var errmsg="";
	var focusid="";
	if($("#country").val()=='')
	{
		validata=false;
		focusid="country";
		if(errmsg=='')
		{
			errmsg="Please Select Country First";
		}
		else
		{
			errmsg="<br>Please Select Country First";
		}
	}
	if(validata==false)
	{
		 $('#'+focusid).next('span').html(data.error_msg);
		 $("#"+focusid).focus();
	}
	else
	{
		$.ajax({
		   url:atob(atob($("#fUrl").val())),
		   type:'post',
		   data:{"txtCountry":Id},
		   error:function(xmlHttpRequest,textStatus,errorThrown)
		   {
			   if(xmlHttpRequest.status==404)
			   {
				   toastr.error("Page Not Found");
			   }
			   else if(xmlHttpRequest.status==500)
			   {
				   toastr.error("Internal Server Error");
			   }
			   else
			   {
				   toastr.error('status:' + XMLHttpRequest.status + ', status text: ' + XMLHttpRequest.statusText);
			   }
		   },
		   success: function(response)
			{
				     
					var data=JSON.parse(response);
					if(data.error)
					{
					  toastr.error(data.error_msg);  
					}
					else
					{
						$("#state").html(data.error_msg);
						
					}
				
				
			}
	    });
	}
	
}
function FetchCity(Id)
{
	var validata=true;
	var errmsg="";
	var focusid="";
	//alert(Id);
	
	
		$.ajax({
		   url:atob(atob($("#fCityUrl").val())),
		   type:'post',
		   data:{"txtState":Id},
		   error:function(xmlHttpRequest,textStatus,errorThrown)
		   {
			   if(xmlHttpRequest.status==404)
			   {
				   toastr.error("Page Not Found");
			   }
			   else if(xmlHttpRequest.status==500)
			   {
				   toastr.error("Internal Server Error");
			   }
			   else
			   {
				   toastr.error('status:' + XMLHttpRequest.status + ', status text: ' + XMLHttpRequest.statusText);
			   }
		   },
		   success: function(response)
			{
				   
					var data=JSON.parse(response);
					if(data.error)
					{
					  toastr.error(data.error_msg);  
					}
					else
					{
						$("#city").html(data.error_msg);
						
					}
				
				
			}
	    });
	
	
}
</script>
<script>
    function AvoidSpace(event) {
    var k = event ? event.which : window.event.keyCode;
    if (k == 32) return false;
    if (k == 34) return false;
    if (k == 39) return false;
}
</script>
<script>
    function AvoidChars(event) {
    var k = event ? event.which : window.event.keyCode;
    
    if (k == 34) return false;
    
}
</script>
</html>
