### 通用非业务错误码

```java
public enum StatusCode {

	SUCCESS(0, "Success"),
	ERROR(1, "System error"),
	AUTHZ_ERR(10, "Authz err"),
	AUTHC_ERR(11, "Authc err"),
	ILLEGAL_REQ(19, "非法请求"),
	ILLEGAL_PARAM(20, "Illegal param"),
	UN_AUTHEN(30, "未经认证"),
	BUSINESS_ERR(40, "业务异常");

	private int code;
	private String msg;

	StatusCode(int code, String msg) {
		this.code = code;
		this.msg = msg;
	}

	public int getCode() {
		return code;
	}

	public String getMsg() {
		return msg;
	}

	public static String getMsg(int code) {
		StatusCode[] enums = StatusCode.values();
		for (StatusCode en : enums) {
			if (code == en.getCode()) {
				return en.getMsg();
			}
		}
		throw new IllegalArgumentException("Illegal code: " + code);
	}

}

```

### 根据执行结果返回状态码，信息，数据。

```java
import XXX.XXX.StatusCode; //改为自己的路径
import io.swagger.annotations.ApiModel;
import io.swagger.annotations.ApiModelProperty;
import lombok.Data;

/**
 * 根据执行结果返回状态码，信息，数据。
 * @param <T>
 */
@ApiModel
@Data
public class ResultData<T> {

	@ApiModelProperty("响应码, 0为成功，其它为失败")
	protected int code;

	@ApiModelProperty("响应消息, 当code不为0时，此为失败消息")
	protected String msg;

	@ApiModelProperty("响应数据, 成功时返回的数据对象")
	protected T data;

	public ResultData() {
		this.msg = StatusCode.SUCCESS.getMsg();
	}

	public ResultData(T data) {
		this();
		this.data = data;
	}

	public ResultData(int code, String msg) {
		this.code = code;
		this.msg = msg;
	}

	/**
	 * 静态构建方法
	 * @return
	 */
	public static <T> ResultData<T> of() {
		return new ResultData<>(StatusCode.SUCCESS.getCode(), StatusCode.SUCCESS.getMsg());
	}

	/**
	 * 静态构建方法
	 *
	 * @param data
	 * @return
	 */
	public static <T> ResultData<T> of(T data) {
		return new ResultData<>(data);
	}

	/**
	 * 静态构建方法
	 *
	 * @param code
	 * @param msg
	 * @return
	 */
	public static <T> ResultData<T> of(int code, String msg) {
		return new ResultData<>(code, msg);
	}

}
```