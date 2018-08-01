---�����������������ʱ�����ù�����---
��̬�����͹������и���ͬ�ľ����ԣ����ܺܺõ���չ�������Ŀ�ѡ������
���磺
public class NutritionFacts {
	private final int servingSize;     // required
	private final int servings;      // required
	private final int calories;     // optional
	private final int fat;          // optional
	private final int sodium;       // optional
	private final int carbohydrate;   // optional

	public NutritionFacts(int servingSize, int servings) {
		this(servingSize, servings, 0);
	}

	public NutritionFacts(int servingSize, int servings, int calories) {
		this(servingSize, servings, calories, 0);
	}

	public NutritionFacts(int servingSize, int servings, int calories, int fat) {
		this(servingSize, servings, calories, fat, 0);
	}

	public NutritionFacts(int servingSize, int servings, int calories, int fat, int sodium) {
		this(servingSize, servings, calories, fat, sodium, 0);
	}

	public NutritionFacts(int servingSize, int servings, int calories, int fat, int sodium, int cabohydrate) {
		this.servingSize = servingSize;
		this.srvings = servings;
		this.calories = calories;
		this.fat = fat;
		this.sodium = sodium;
		this.carbohydrate = carbohydrate;

	}
}
����Ҫ����NutritionFacts��ʵ����ʱ�򣬾����ò����б���̵Ĺ������������б������Ҫ���õ����в�����
�������������ͨ����Ҫ����㱾�������õĲ��������ǻ��ǲ��ò�Ϊ���Ǵ���ֵ��

�ɴ˿ɼ����ص�������ģʽ���У����ǵ�����������ʱ�򣬿ͻ��˴���ͺ��ѱ�д�����������Ķ���

�Ľ��ķ���---JavaBeansģʽ
����һ���޲ι���������������Ȼ�����setter����������ÿ����Ҫ�Ĳ�����
public class NutritionFacts {
	private final int servingSize = -1;     // required
	private final int servings = -1;      // required
	private final int calories = 0;     // optional
	private final int fat = 0;          // optional
	private final int sodium = 0;       // optional
	private final int carbohydrate = 0;   // optional

	public NutritionFacts(){}

	// setters
	public void setServingSize(int val) { servingSize = val;}
	// .....

}
����ģʽ�´���ʵ����
NutritionFacts fact = new NutritionFacts();
fact.setServingSize(250);
//....
����ģʽ�����ص�ȱ���ǣ�������̱��ֵ��˼��������У��ڹ�����JavaBean���ܴ��ڲ�һ�µ�״̬��

�ռ�����---Builderģʽ��ʾ����
public class NutritionFacts {
	private final int servingSize;     // required
	private final int servings;      // required
	private final int calories;     // optional
	private final int fat;          // optional
	private final int sodium;       // optional
	private final int carbohydrate;   // optional
	
	public static class Builder {
		private final int servingSize;     // required
		private final int servings;      // required

		private int calories = 0;     // optional
		private int fat = 0;          // optional
		private int sodium = 0;       // optional
		private int carbohydrate = 0;   // optional

		publilc Builder(int servingSize, int servings) {
			this.servingSize = servingSize;
			this.servings = servings;
		}

		public Builder calories(int val) {
			calories = val;
			return this;
		}

		public Builder fat(int val) {
			fat = val;
			return this;
		}

		public Builder carbohydrate(int val) {
			carbohydrate = val;
			return this;
		}

		public Builder sodium(int val) {
			sodium = val;
			return this;
		}
		
		public NutritionFacts build() {
			return new NutritionFacts(this);
		}
	}

	private NutritionFacts(Builder builder) {
		servingSize = builder.servingSize;
		servings = builder.servings;
		calories = builder.calories;
		fat = builder.fat;
		sodium = builder.sodium;
		carbohydrate = builer.carbohydrate;
	}
}
����NutritionFacts�ǲ��ɱ�ģ�����Ĭ�ϵĲ���ֵ����������һ���ط���builder��setter��������builder
�����Ա���԰ѵ���������������������ʵ����
NutritionFacts coca = new NutritionFacts.Builder(290, 5).calories(90),sodium(33),carbohydrate(22).builder();


