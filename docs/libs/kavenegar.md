# Kavenegar

[kavenegra](http://kavenegar.com) is an sms panel service to implement the sms notifications inside the project. for actions like `new visit`, `registered` or ... . this service provides some rest apis to work with. we used 2 apis in this proeject:

## Verification

verify operation in kavenegar is used for registering users. register token sms in this service is very important and we have to make sure that sms is delivered to user's phone. so we use the `lookup` api. `lookup` api uses a pattern and send to token to the phone number that user sent. if there was any problems, kavenegar calls user's phone and plays a voice that spells the token fotr him