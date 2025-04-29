# IEEE-CIS-Fraud-Detection

## პროექტის მიზანი
IEEE-CIS Fraud Detection კონკურსი მიზნად ისახავს საეჭვო ტრანზაქციების დეტექციისთვის მოდელების შემუშავებას. კონკურსში წარმოდგენილია რეალური ტრანზაქციული მონაცემები Vesta Corporation-ისგან. ჩვენი ამოცანაა დავადგინოთ არის თუ არა კონკრეტული ტრანზაქცია თაღლითური.

## რეპოზიტორიის სტრუქტურა
1. model-experiment-linearRegression : ლოგისტიკური რეგრესიის მოდელის შექმნა და ანალიზი.
2. model-experiment-xgboost : XGBoost მოდელის შექმნის პროცესი, მონაცემების გაწმენდა, Feature Engineering, მოდელის დატრენინგება და პარამეტრების ოპტიმიზაცია.
3. model-inference :  საუკეთესო მოდელით ტესტინგ მონაცემების გამოყენებით პროგნოზირება.
4. README.md: პროექტის დეტალური აღწერა და შედეგების შეჯამება.

## Feature Engineering
1. კატეგორიული ცვლადების რიცხვითში გადაყვანა
   გამოვიყენე LabelEncoder კატეგორიული ცვლადების რიცხვით ცვლადებში გადასაყვანად.
2. Nan მნიშვნელობების დამუშავება
   მთლიანად წავშალე ის სვეტები, რომლებშიც 90%-ზე მეტი მნიშვნელობა NaN იყო...
   რიცხვითი ცვლადებისთვის გამოვიყენე -999, როგორც განსხვავებული მნიშვნელობა NaN-ების გადასაფარად
   კატეგორიული ცვლადებისთვის კი NaN მნიშვნელობები გადავფარე "unknown"-ით
4. მეხსიერების ოპტიმიზაციისთვის გამოვიყენე reduce_mem_usage ფუნქცია, რომელიც ამცირებს DataFrame-ის მიერ გამოყენებულ მეხსიერებას მონაცემთა ტიპების ოპტიმიზაციით.
   წავშალე TransactionID და TransactionDT სვეტებიც.

## Feature Selection
ამ ნაწილში კი საწყისი ცვლადებიდან შევარჩიე 100 ყველაზე მნიშვნელოვანი, რათა თავიდან ამერიდებინა მოდელის კომპლექსურობა\

## Training

ტესტირებული მოდელები:
   1. XGBoost: მოდელი, რომელიც კარგად მუშაობს არაწრფივ მონაცემებზე.
   2. Logistic Regression: სწრაფი და ინტერპრეტირებადი მოდელი, თუმცა საკმაოდ არაზუსტი...

XGBoost შევარჩიე საბოლოო მოდელად შემდეგი მიზეზების გამო:
1. XGBoost-მა აჩვენა სანდო შედეგები ვიდრე Logistic Regression-მა 
2. XGBoost-ს შეუძლია კომპლექსური ურთიერთდამოკიდებულებების უკეთესად 'დაჭერა', ვიდრე ლოგისტიკურ რეგრესიას

## MLFlow Tracking
ექსპერიმენტები DagsHub-ზე:
https://dagshub.com/jgushiann/IEEE-CIS-Fraud-Detection/experiments

https://dagshub.com/jgushiann/IEEE-CIS-Fraud-Detection.mlflow/#/experiments/0?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D

https://dagshub.com/jgushiann/IEEE-CIS-Fraud-Detection.mlflow/#/experiments/1?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D
