<template>
  <div class="addEdit-block">
    <el-form
      class="detail-form-content"
      ref="ruleForm"
      :model="ruleForm"
      :rules="rules"
      label-width="80px"
	  :style="{backgroundColor:addEditForm.addEditBoxColor}"
    >
      <el-row>
                        <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="商家账号" prop="shangjiazhanghao">
          <el-input v-model="ruleForm.shangjiazhanghao" 
              placeholder="商家账号" clearable  :readonly="ro.shangjiazhanghao"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="商家账号" prop="shangjiazhanghao">
              <el-input v-model="ruleForm.shangjiazhanghao" 
                placeholder="商家账号" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
                                    <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="商家姓名" prop="shangjiaxingming">
          <el-input v-model="ruleForm.shangjiaxingming" 
              placeholder="商家姓名" clearable  :readonly="ro.shangjiaxingming"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="商家姓名" prop="shangjiaxingming">
              <el-input v-model="ruleForm.shangjiaxingming" 
                placeholder="商家姓名" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
                                    <el-col :span="12">
        <el-form-item class="select" v-if="type!='info'" label="店铺名称" prop="dianpumingcheng">
          <el-select  @change="dianpumingchengChange" v-model="ruleForm.dianpumingcheng" placeholder="请选择店铺名称">
            <el-option
                v-for="(item,index) in dianpumingchengOptions"
                v-bind:key="index"
                :label="item"
                :value="item">
            </el-option>
          </el-select>
        </el-form-item>
        <div v-else>
          <el-form-item class="input"v-if="ruleForm.dianpumingcheng" label="店铺名称" prop="dianpumingcheng">
              <el-input v-model="ruleForm.dianpumingcheng" 
                placeholder="店铺名称" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
                                    <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="外卖名称" prop="waimaimingcheng">
          <el-input v-model="ruleForm.waimaimingcheng" 
              placeholder="外卖名称" clearable  :readonly="ro.waimaimingcheng"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="外卖名称" prop="waimaimingcheng">
              <el-input v-model="ruleForm.waimaimingcheng" 
                placeholder="外卖名称" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
                                    <el-col :span="12">
        <el-form-item class="select" v-if="type!='info'"  label="分类" prop="fenlei">
          <el-select v-model="ruleForm.fenlei" placeholder="请选择分类">
            <el-option
                v-for="(item,index) in fenleiOptions"
                v-bind:key="index"
                :label="item"
                :value="item">
            </el-option>
          </el-select>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="分类" prop="fenlei">
	      <el-input v-model="ruleForm.fenlei"
                placeholder="分类" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
                                    <el-col :span="24">  
        <el-form-item class="upload" v-if="type!='info' && !ro.waimaifengmian" label="外卖封面" prop="waimaifengmian">
          <file-upload
          tip="点击上传外卖封面"
          action="file/upload"
          :limit="3"
          :multiple="true"
          :fileUrls="ruleForm.waimaifengmian?ruleForm.waimaifengmian:''"
          @change="waimaifengmianUploadChange"
          ></file-upload>
        </el-form-item>
        <div v-else>
          <el-form-item v-if="ruleForm.waimaifengmian" label="外卖封面" prop="waimaifengmian">
            <img style="margin-right:20px;" v-bind:key="index" v-for="(item,index) in ruleForm.waimaifengmian.split(',')" :src="item" width="100" height="100">
          </el-form-item>
        </div>
      </el-col>
                                    <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="外卖分量" prop="waimaifenliang">
          <el-input v-model="ruleForm.waimaifenliang" 
              placeholder="外卖分量" clearable  :readonly="ro.waimaifenliang"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="外卖分量" prop="waimaifenliang">
              <el-input v-model="ruleForm.waimaifenliang" 
                placeholder="外卖分量" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
                                                                                                <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="月售数量" prop="yueshoushuliang">
          <el-input v-model="ruleForm.yueshoushuliang" 
              placeholder="月售数量" clearable  :readonly="ro.yueshoushuliang"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="月售数量" prop="yueshoushuliang">
              <el-input v-model="ruleForm.yueshoushuliang" 
                placeholder="月售数量" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
                                    <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="配送价格" prop="peisongjiage">
          <el-input v-model="ruleForm.peisongjiage" 
              placeholder="配送价格" clearable  :readonly="ro.peisongjiage"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="配送价格" prop="peisongjiage">
              <el-input v-model="ruleForm.peisongjiage" 
                placeholder="配送价格" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
                                    <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="起送价格" prop="qisongjiage">
          <el-input v-model="ruleForm.qisongjiage" 
              placeholder="起送价格" clearable  :readonly="ro.qisongjiage"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="起送价格" prop="qisongjiage">
              <el-input v-model="ruleForm.qisongjiage" 
                placeholder="起送价格" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
                                    <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="配送时间" prop="peisongshijian">
          <el-input v-model="ruleForm.peisongshijian" 
              placeholder="配送时间" clearable  :readonly="ro.peisongshijian"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="配送时间" prop="peisongshijian">
              <el-input v-model="ruleForm.peisongshijian" 
                placeholder="配送时间" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
                                                                                                                                                            <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="价格" prop="price">
          <el-input v-model="ruleForm.price" 
              placeholder="价格" clearable  :readonly="ro.price"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="价格" prop="price">
              <el-input v-model="ruleForm.price" 
                placeholder="价格" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
                              </el-row>
                                                                                                                          <el-row>
            <el-col :span="24">
              <el-form-item class="textarea" v-if="type!='info'" label="外卖主料" prop="waimaizhuliao">
                <el-input
                  style="min-width: 200px; max-width: 600px;"
                  type="textarea"
                  :rows="8"
                  placeholder="外卖主料"
                  v-model="ruleForm.waimaizhuliao" >
                </el-input>
              </el-form-item>
              <div v-else>
                <el-form-item v-if="ruleForm.waimaizhuliao" label="外卖主料" prop="waimaizhuliao">
                    <span>{{ruleForm.waimaizhuliao}}</span>
                </el-form-item>
              </div>
            </el-col>
          </el-row>
                                <el-row>
            <el-col :span="24">
              <el-form-item class="textarea" v-if="type!='info'" label="外卖详情" prop="waimaixiangqing">
                <el-input
                  style="min-width: 200px; max-width: 600px;"
                  type="textarea"
                  :rows="8"
                  placeholder="外卖详情"
                  v-model="ruleForm.waimaixiangqing" >
                </el-input>
              </el-form-item>
              <div v-else>
                <el-form-item v-if="ruleForm.waimaixiangqing" label="外卖详情" prop="waimaixiangqing">
                    <span>{{ruleForm.waimaixiangqing}}</span>
                </el-form-item>
              </div>
            </el-col>
          </el-row>
                                                                                                                                                                                                                                                                                                                                                                                                                    <el-form-item class="btn">
                <el-button v-if="type!='info'" type="primary" class="btn-success" @click="onSubmit">提交</el-button>
        <el-button v-if="type!='info'" class="btn-close" @click="back()">取消</el-button>
        <el-button v-if="type=='info'" class="btn-close" @click="back()">返回</el-button>
      </el-form-item>
    </el-form>
    
    
  </div>
</template>
<script>
// 数字，邮件，手机，url，身份证校验
import { isNumber,isIntNumer,isEmail,isPhone, isMobile,isURL,checkIdCard } from "@/utils/validate";
export default {
  data() {
    let self = this
    var validateIdCard = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!checkIdCard(value)) {
        callback(new Error("请输入正确的身份证号码"));
      } else {
        callback();
      }
    };
    var validateUrl = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!isURL(value)) {
        callback(new Error("请输入正确的URL地址"));
      } else {
        callback();
      }
    };
    var validateMobile = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!isMobile(value)) {
        callback(new Error("请输入正确的手机号码"));
      } else {
        callback();
      }
    };
    var validatePhone = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!isPhone(value)) {
        callback(new Error("请输入正确的电话号码"));
      } else {
        callback();
      }
    };
    var validateEmail = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!isEmail(value)) {
        callback(new Error("请输入正确的邮箱地址"));
      } else {
        callback();
      }
    };
    var validateNumber = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!isNumber(value)) {
        callback(new Error("请输入数字"));
      } else {
        callback();
      }
    };
    var validateIntNumber = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!isIntNumer(value)) {
        callback(new Error("请输入整数"));
      } else {
        callback();
      }
    };
    return {
	  addEditForm: {"btnSaveFontColor":"#fff","selectFontSize":"14px","btnCancelBorderColor":"rgba(152, 129, 129, 1)","inputBorderRadius":"22px","inputFontSize":"14px","textareaBgColor":"#fff","btnSaveFontSize":"14px","textareaBorderRadius":"22px","uploadBgColor":"#fff","textareaBorderStyle":"solid","btnCancelWidth":"88px","textareaHeight":"120px","dateBgColor":"#fff","btnSaveBorderRadius":"22px","uploadLableFontSize":"14px","textareaBorderWidth":"1px","inputLableColor":"#606266","addEditBoxColor":"rgba(210, 194, 194, 0.29)","dateIconFontSize":"14px","btnSaveBgColor":"#409EFF","uploadIconFontColor":"#8c939d","textareaBorderColor":"rgba(152, 129, 129, 1)","btnCancelBgColor":"rgba(143, 222, 143, 1)","selectLableColor":"#606266","btnSaveBorderStyle":"solid","dateBorderWidth":"1px","dateLableFontSize":"14px","dateBorderRadius":"22px","btnCancelBorderStyle":"solid","selectLableFontSize":"14px","selectBorderStyle":"solid","selectIconFontColor":"#C0C4CC","btnCancelHeight":"44px","inputHeight":"40px","btnCancelFontColor":"#606266","dateBorderColor":"rgba(152, 129, 129, 1)","dateIconFontColor":"#C0C4CC","uploadBorderStyle":"solid","dateBorderStyle":"solid","dateLableColor":"#606266","dateFontSize":"14px","inputBorderWidth":"1px","uploadIconFontSize":"28px","selectHeight":"40px","inputFontColor":"#606266","uploadHeight":"148px","textareaLableColor":"#606266","textareaLableFontSize":"14px","btnCancelFontSize":"14px","inputBorderStyle":"solid","btnCancelBorderRadius":"22px","inputBgColor":"rgba(252, 250, 250, 1)","inputLableFontSize":"14px","uploadLableColor":"#606266","uploadBorderRadius":"22px","btnSaveHeight":"44px","selectBgColor":"#fff","btnSaveWidth":"88px","selectIconFontSize":"14px","dateHeight":"40px","selectBorderColor":"rgba(152, 129, 129, 1)","inputBorderColor":"rgba(152, 129, 129, 1)","uploadBorderColor":"rgba(152, 129, 129, 1)","textareaFontColor":"#606266","selectBorderWidth":"1px","dateFontColor":"#606266","btnCancelBorderWidth":"1px","uploadBorderWidth":"1px","textareaFontSize":"14px","selectBorderRadius":"22px","selectFontColor":"#606266","btnSaveBorderColor":"#409EFF","btnSaveBorderWidth":"1px"},
      id: '',
      type: '',
      ro:{
	shangjiazhanghao : false,
	shangjiaxingming : false,
	dianpumingcheng : false,
	waimaimingcheng : false,
	fenlei : false,
	waimaifengmian : false,
	waimaifenliang : false,
	waimaizhuliao : false,
	waimaixiangqing : false,
	yueshoushuliang : false,
	peisongjiage : false,
	qisongjiage : false,
	peisongshijian : false,
	thumbsupnum : false,
	crazilynum : false,
	clicktime : false,
	clicknum : false,
	price : false,
      },
            ruleForm: {
                	        shangjiazhanghao: '',
	                        	        shangjiaxingming: '',
	                        	        dianpumingcheng: '',
	                        	        waimaimingcheng: '',
	                        	        fenlei: '',
	                        	        waimaifengmian: '',
	                        	        waimaifenliang: '',
	                        	        waimaizhuliao: '',
	                        	        waimaixiangqing: '',
	                        	        yueshoushuliang: '',
	                        	        peisongjiage: '',
	                        	        qisongjiage: '',
	                        	        peisongshijian: '',
	                        	                        	                        	        clicktime: '',
	                        	                        	        price: '',
	                      },
                                                    dianpumingchengOptions: [],
                                              fenleiOptions: [],
                                                                                                                                                                                                          rules: {
                  shangjiazhanghao: [
                                    	                                                              ],
                  shangjiaxingming: [
                                    	                                                              ],
                  dianpumingcheng: [
                                    	                                                              ],
                  waimaimingcheng: [
                                    	                                                              ],
                  fenlei: [
                                    	                                                              ],
                  waimaifengmian: [
                                    	                                                              ],
                  waimaifenliang: [
                                    	                                                              ],
                  waimaizhuliao: [
                                    	                                                              ],
                  waimaixiangqing: [
                                    	                                                              ],
                  yueshoushuliang: [
                                    	                                                              ],
                  peisongjiage: [
                                        { validator: validateIntNumber, trigger: 'blur' },
                        	                                                              ],
                  qisongjiage: [
                                        { validator: validateIntNumber, trigger: 'blur' },
                        	                                                              ],
                  peisongshijian: [
                            { required: true, message: '配送时间不能为空', trigger: 'blur' },
                                    	                                                              ],
                  thumbsupnum: [
                                        { validator: validateIntNumber, trigger: 'blur' },
                        	                                                              ],
                  crazilynum: [
                                        { validator: validateIntNumber, trigger: 'blur' },
                        	                                                              ],
                  clicktime: [
                                    	                                                              ],
                  clicknum: [
                                        { validator: validateIntNumber, trigger: 'blur' },
                        	                                                              ],
                  price: [
                            { required: true, message: '价格不能为空', trigger: 'blur' },
                                                    { validator: validateNumber, trigger: 'blur' },
            	                                                              ],
              }
    };
  },
  props: ["parent"],
  computed: {
                                                                                                                                                                                                                              },
  created() {
	this.addEditStyleChange()
	this.addEditUploadStyleChange()
  },
  methods: {
        // 下载
    download(file){
      window.open(`${file}`)
    },
    // 初始化
    init(id,type) {
      if (id) {
        this.id = id;
        this.type = type;
      }
      if(this.type=='info'||this.type=='else'){
        this.info(id);
      }else if(this.type=='cross'){
        var obj = this.$storage.getObj('crossObj');
        for (var o in obj){
          	            if(o=='shangjiazhanghao'){
            this.ruleForm.shangjiazhanghao = obj[o];
	    this.ro.shangjiazhanghao = true;
            continue;
          }
	            	            if(o=='shangjiaxingming'){
            this.ruleForm.shangjiaxingming = obj[o];
	    this.ro.shangjiaxingming = true;
            continue;
          }
	            	            if(o=='dianpumingcheng'){
            this.ruleForm.dianpumingcheng = obj[o];
	    this.ro.dianpumingcheng = true;
            continue;
          }
	            	            if(o=='waimaimingcheng'){
            this.ruleForm.waimaimingcheng = obj[o];
	    this.ro.waimaimingcheng = true;
            continue;
          }
	            	            if(o=='fenlei'){
            this.ruleForm.fenlei = obj[o];
	    this.ro.fenlei = true;
            continue;
          }
	            	            if(o=='waimaifengmian'){
            this.ruleForm.waimaifengmian = obj[o];
	    this.ro.waimaifengmian = true;
            continue;
          }
	            	            if(o=='waimaifenliang'){
            this.ruleForm.waimaifenliang = obj[o];
	    this.ro.waimaifenliang = true;
            continue;
          }
	            	            if(o=='waimaizhuliao'){
            this.ruleForm.waimaizhuliao = obj[o];
	    this.ro.waimaizhuliao = true;
            continue;
          }
	            	            if(o=='waimaixiangqing'){
            this.ruleForm.waimaixiangqing = obj[o];
	    this.ro.waimaixiangqing = true;
            continue;
          }
	            	            if(o=='yueshoushuliang'){
            this.ruleForm.yueshoushuliang = obj[o];
	    this.ro.yueshoushuliang = true;
            continue;
          }
	            	            if(o=='peisongjiage'){
            this.ruleForm.peisongjiage = obj[o];
	    this.ro.peisongjiage = true;
            continue;
          }
	            	            if(o=='qisongjiage'){
            this.ruleForm.qisongjiage = obj[o];
	    this.ro.qisongjiage = true;
            continue;
          }
	            	            if(o=='peisongshijian'){
            this.ruleForm.peisongshijian = obj[o];
	    this.ro.peisongshijian = true;
            continue;
          }
	            	            if(o=='thumbsupnum'){
            this.ruleForm.thumbsupnum = obj[o];
	    this.ro.thumbsupnum = true;
            continue;
          }
	            	            if(o=='crazilynum'){
            this.ruleForm.crazilynum = obj[o];
	    this.ro.crazilynum = true;
            continue;
          }
	            	            if(o=='clicktime'){
            this.ruleForm.clicktime = obj[o];
	    this.ro.clicktime = true;
            continue;
          }
	            	            if(o=='clicknum'){
            this.ruleForm.clicknum = obj[o];
	    this.ro.clicknum = true;
            continue;
          }
	            	            if(o=='price'){
            this.ruleForm.price = obj[o];
	    this.ro.price = true;
            continue;
          }
	                    }
                                                                                                                                                                                                                                                                                                              }
            // 获取用户信息
      this.$http({
        url: `${this.$storage.get('sessionTable')}/session`,
        method: "get"
      }).then(({ data }) => {
        if (data && data.code === 0) {
          var json = data.data;
                                                                                                                                                                                                                                                                                                                                                                                                                              } else {
          this.$message.error(data.msg);
        }
      });
                                                                              this.$http({
              url: `option/shanghuxinxi/dianpumingcheng`,
              method: "get"
            }).then(({ data }) => {
              if (data && data.code === 0) {
                this.dianpumingchengOptions = data.data;
              } else {
                this.$message.error(data.msg);
              }
            });
                                                          this.$http({
              url: `option/shipinfenlei/fenlei`,
              method: "get"
            }).then(({ data }) => {
              if (data && data.code === 0) {
                this.fenleiOptions = data.data;
              } else {
                this.$message.error(data.msg);
              }
            });
         
                                                                                                                                                                                                                                                                      },
                            // 下二随
    dianpumingchengChange () {
      this.$http({
        url: `follow/shanghuxinxi/dianpumingcheng?columnValue=`+ this.ruleForm.dianpumingcheng,
        method: "get"
      }).then(({ data }) => {
        if (data && data.code === 0) {
                                    if(data.data.shangjiazhanghao){
                this.ruleForm.shangjiazhanghao = data.data.shangjiazhanghao
              }
                                                if(data.data.shangjiaxingming){
                this.ruleForm.shangjiaxingming = data.data.shangjiaxingming
              }
                                                                                                                                                                                                          if(data.data.yueshoushuliang){
                this.ruleForm.yueshoushuliang = data.data.yueshoushuliang
              }
                                                if(data.data.peisongjiage){
                this.ruleForm.peisongjiage = data.data.peisongjiage
              }
                                                if(data.data.qisongjiage){
                this.ruleForm.qisongjiage = data.data.qisongjiage
              }
                                                                                                                                                                  } else {
          this.$message.error(data.msg);
        }
      });
    },
                                                                                                                                    // 多级联动参数
                                                                                                                                                                                                info(id) {
      this.$http({
        url: `waimaixinxi/info/${id}`,
        method: "get"
      }).then(({ data }) => {
        if (data && data.code === 0) {
        this.ruleForm = data.data;
	//解决前台上传图片后台不显示的问题
	let reg=new RegExp('../../../upload','g')//g代表全部
        } else {
          this.$message.error(data.msg);
        }
      });
    },
        // 提交
    onSubmit() {
                  // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                              // ${column.compare}
                                                                                                                                                                                                                                                                                                                                                                        this.$refs["ruleForm"].validate(valid => {
        if (valid) {
          this.$http({
            url: `waimaixinxi/${!this.ruleForm.id ? "save" : "update"}`,
            method: "post",
            data: this.ruleForm
          }).then(({ data }) => {
            if (data && data.code === 0) {
              this.$message({
                message: "操作成功",
                type: "success",
                duration: 1500,
                onClose: () => {
                  this.parent.showFlag = true;
                  this.parent.addOrUpdateFlag = false;
                  this.parent.waimaixinxiCrossAddOrUpdateFlag = false;
                  this.parent.search();
                  this.parent.contentStyleChange();
                }
              });
            } else {
              this.$message.error(data.msg);
            }
          });
        }
      });
    },
    // 获取uuid
    getUUID () {
      return new Date().getTime();
    },
    // 返回
    back() {
      this.parent.showFlag = true;
      this.parent.addOrUpdateFlag = false;
      this.parent.waimaixinxiCrossAddOrUpdateFlag = false;
      this.parent.contentStyleChange();
    },
                                                                                    waimaifengmianUploadChange(fileUrls) {
                this.ruleForm.waimaifengmian = fileUrls;
				this.addEditUploadStyleChange()
            },
                                                                                                                                                            	addEditStyleChange() {
	  this.$nextTick(()=>{
	    // input
	    document.querySelectorAll('.addEdit-block .input .el-input__inner').forEach(el=>{
	      el.style.height = this.addEditForm.inputHeight
	      el.style.color = this.addEditForm.inputFontColor
	      el.style.fontSize = this.addEditForm.inputFontSize
	      el.style.borderWidth = this.addEditForm.inputBorderWidth
	      el.style.borderStyle = this.addEditForm.inputBorderStyle
	      el.style.borderColor = this.addEditForm.inputBorderColor
	      el.style.borderRadius = this.addEditForm.inputBorderRadius
	      el.style.backgroundColor = this.addEditForm.inputBgColor
	    })
	    document.querySelectorAll('.addEdit-block .input .el-form-item__label').forEach(el=>{
	      el.style.lineHeight = this.addEditForm.inputHeight
	      el.style.color = this.addEditForm.inputLableColor
	      el.style.fontSize = this.addEditForm.inputLableFontSize
	    })
	    // select
	    document.querySelectorAll('.addEdit-block .select .el-input__inner').forEach(el=>{
	      el.style.height = this.addEditForm.selectHeight
	      el.style.color = this.addEditForm.selectFontColor
	      el.style.fontSize = this.addEditForm.selectFontSize
	      el.style.borderWidth = this.addEditForm.selectBorderWidth
	      el.style.borderStyle = this.addEditForm.selectBorderStyle
	      el.style.borderColor = this.addEditForm.selectBorderColor
	      el.style.borderRadius = this.addEditForm.selectBorderRadius
	      el.style.backgroundColor = this.addEditForm.selectBgColor
	    })
	    document.querySelectorAll('.addEdit-block .select .el-form-item__label').forEach(el=>{
	      el.style.lineHeight = this.addEditForm.selectHeight
	      el.style.color = this.addEditForm.selectLableColor
	      el.style.fontSize = this.addEditForm.selectLableFontSize
	    })
	    document.querySelectorAll('.addEdit-block .select .el-select__caret').forEach(el=>{
	      el.style.color = this.addEditForm.selectIconFontColor
	      el.style.fontSize = this.addEditForm.selectIconFontSize
	    })
	    // date
	    document.querySelectorAll('.addEdit-block .date .el-input__inner').forEach(el=>{
	      el.style.height = this.addEditForm.dateHeight
	      el.style.color = this.addEditForm.dateFontColor
	      el.style.fontSize = this.addEditForm.dateFontSize
	      el.style.borderWidth = this.addEditForm.dateBorderWidth
	      el.style.borderStyle = this.addEditForm.dateBorderStyle
	      el.style.borderColor = this.addEditForm.dateBorderColor
	      el.style.borderRadius = this.addEditForm.dateBorderRadius
	      el.style.backgroundColor = this.addEditForm.dateBgColor
	    })
	    document.querySelectorAll('.addEdit-block .date .el-form-item__label').forEach(el=>{
	      el.style.lineHeight = this.addEditForm.dateHeight
	      el.style.color = this.addEditForm.dateLableColor
	      el.style.fontSize = this.addEditForm.dateLableFontSize
	    })
	    document.querySelectorAll('.addEdit-block .date .el-input__icon').forEach(el=>{
	      el.style.color = this.addEditForm.dateIconFontColor
	      el.style.fontSize = this.addEditForm.dateIconFontSize
	      el.style.lineHeight = this.addEditForm.dateHeight
	    })
	    // upload
	    let iconLineHeight = parseInt(this.addEditForm.uploadHeight) - parseInt(this.addEditForm.uploadBorderWidth) * 2 + 'px'
	    document.querySelectorAll('.addEdit-block .upload .el-upload--picture-card').forEach(el=>{
	      el.style.width = this.addEditForm.uploadHeight
	      el.style.height = this.addEditForm.uploadHeight
	      el.style.borderWidth = this.addEditForm.uploadBorderWidth
	      el.style.borderStyle = this.addEditForm.uploadBorderStyle
	      el.style.borderColor = this.addEditForm.uploadBorderColor
	      el.style.borderRadius = this.addEditForm.uploadBorderRadius
	      el.style.backgroundColor = this.addEditForm.uploadBgColor
	    })
	    document.querySelectorAll('.addEdit-block .upload .el-form-item__label').forEach(el=>{
	      el.style.lineHeight = this.addEditForm.uploadHeight
	      el.style.color = this.addEditForm.uploadLableColor
	      el.style.fontSize = this.addEditForm.uploadLableFontSize
	    })
	    document.querySelectorAll('.addEdit-block .upload .el-icon-plus').forEach(el=>{
	      el.style.color = this.addEditForm.uploadIconFontColor
	      el.style.fontSize = this.addEditForm.uploadIconFontSize
	      el.style.lineHeight = iconLineHeight
	      el.style.display = 'block'
	    })
	    // 多文本输入框
	    document.querySelectorAll('.addEdit-block .textarea .el-textarea__inner').forEach(el=>{
	      el.style.height = this.addEditForm.textareaHeight
	      el.style.color = this.addEditForm.textareaFontColor
	      el.style.fontSize = this.addEditForm.textareaFontSize
	      el.style.borderWidth = this.addEditForm.textareaBorderWidth
	      el.style.borderStyle = this.addEditForm.textareaBorderStyle
	      el.style.borderColor = this.addEditForm.textareaBorderColor
	      el.style.borderRadius = this.addEditForm.textareaBorderRadius
	      el.style.backgroundColor = this.addEditForm.textareaBgColor
	    })
	    document.querySelectorAll('.addEdit-block .textarea .el-form-item__label').forEach(el=>{
	      // el.style.lineHeight = this.addEditForm.textareaHeight
	      el.style.color = this.addEditForm.textareaLableColor
	      el.style.fontSize = this.addEditForm.textareaLableFontSize
	    })
	    // 保存
	    document.querySelectorAll('.addEdit-block .btn .btn-success').forEach(el=>{
	      el.style.width = this.addEditForm.btnSaveWidth
	      el.style.height = this.addEditForm.btnSaveHeight
	      el.style.color = this.addEditForm.btnSaveFontColor
	      el.style.fontSize = this.addEditForm.btnSaveFontSize
	      el.style.borderWidth = this.addEditForm.btnSaveBorderWidth
	      el.style.borderStyle = this.addEditForm.btnSaveBorderStyle
	      el.style.borderColor = this.addEditForm.btnSaveBorderColor
	      el.style.borderRadius = this.addEditForm.btnSaveBorderRadius
	      el.style.backgroundColor = this.addEditForm.btnSaveBgColor
	    })
	    // 返回
	    document.querySelectorAll('.addEdit-block .btn .btn-close').forEach(el=>{
	      el.style.width = this.addEditForm.btnCancelWidth
	      el.style.height = this.addEditForm.btnCancelHeight
	      el.style.color = this.addEditForm.btnCancelFontColor
	      el.style.fontSize = this.addEditForm.btnCancelFontSize
	      el.style.borderWidth = this.addEditForm.btnCancelBorderWidth
	      el.style.borderStyle = this.addEditForm.btnCancelBorderStyle
	      el.style.borderColor = this.addEditForm.btnCancelBorderColor
	      el.style.borderRadius = this.addEditForm.btnCancelBorderRadius
	      el.style.backgroundColor = this.addEditForm.btnCancelBgColor
	    })
	  })
	},
	addEditUploadStyleChange() {
		this.$nextTick(()=>{
		  document.querySelectorAll('.addEdit-block .upload .el-upload-list--picture-card .el-upload-list__item').forEach(el=>{
			el.style.width = this.addEditForm.uploadHeight
			el.style.height = this.addEditForm.uploadHeight
			el.style.borderWidth = this.addEditForm.uploadBorderWidth
			el.style.borderStyle = this.addEditForm.uploadBorderStyle
			el.style.borderColor = this.addEditForm.uploadBorderColor
			el.style.borderRadius = this.addEditForm.uploadBorderRadius
			el.style.backgroundColor = this.addEditForm.uploadBgColor
		  })
	  })
	},
  }
};
</script>
<style lang="scss">
.editor{
  height: 500px;
  
  & /deep/ .ql-container {
	  height: 310px;
  }
}
.amap-wrapper {
  width: 100%;
  height: 500px;
}
.search-box {
  position: absolute;
}
.addEdit-block {
	margin: -10px;
}
.detail-form-content {
	padding: 12px;
}
.btn .el-button {
  padding: 0;
}
</style>
