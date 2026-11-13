
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>IRON | Smart Iron Monitoring</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

<header>
  <div class="brand">IRON<span>®</span></div>
  <p>Smart Iron Monitoring System</p>
</header>

<main>
  <section class="hero">
    <span class="tag">SMART HEALTHCARE TECHNOLOGY</span>
    <h1>راقب مؤشرات الحديد بذكاء</h1>
    <p>
      نظام ذكي يعتمد على لصقة جلدية مزودة بإبر دقيقة
      وحساسات لمتابعة المؤشرات المرتبطة بالحديد.
    </p>
  </section>

  <section class="section">
    <h2>مكونات نظام IRON</h2>

    <div class="components">

      <div class="component-card">
        <div class="patch">
          <div class="patch-center">IRON</div>
        </div>
        <h3>اللصقة الذكية</h3>
        <p>لصقة دائرية مزودة بإبر دقيقة وحساسات حيوية.</p>
        <span class="status">Microneedle Patch</span>
      </div>

      <div class="component-card">
        <div class="device">
          <div class="device-screen">
            <span>IRON</span>
            <div class="screen-dot"></div>
            <small>SMART DEVICE</small>
          </div>
          <div class="device-button"></div>
        </div>
        <h3>الجهاز الإلكتروني</h3>
        <p>وحدة إلكترونية لمعالجة بيانات الحساس وإرسالها للتطبيق.</p>
        <span class="status">Electronic Unit</span>
      </div>

    </div>
  </section>

  <section class="section">
    <h2>كيف يعمل النظام؟</h2>

    <div class="steps">
      <div class="step">
        <span>01</span>
        <h3>جمع العينة</h3>
        <p>تجمع الإبر الدقيقة السائل الخلالي من الجلد.</p>
      </div>

      <div class="step">
        <span>02</span>
        <h3>تحليل المؤشرات</h3>
        <p>تعمل الحساسات على تحليل المؤشرات المستهدفة.</p>
      </div>

      <div class="step">
        <span>03</span>
        <h3>نقل البيانات</h3>
        <p>يرسل الجهاز الإلكتروني البيانات إلى التطبيق.</p>
      </div>
    </div>
  </section>

  <section class="section dashboard">
    <h2>لوحة متابعة المؤشرات</h2>
    <p class="muted">نموذج توضيحي لواجهة نتائج التطبيق</p>

    <div class="connection">
      <span class="indicator"></span>
      <span id="connectionStatus">الجهاز غير متصل فعليًا</span>
    </div>

    <button id="demoBtn">عرض نموذج قراءة تجريبية</button>

    <div class="reading">
      <div>
        <p>Ferritin</p>
        <h1 id="ferritin">--</h1>
        <small>ng/mL</small>
      </div>
      <div>
        <p>Iron Indicators</p>
        <h3 id="ironStatus">بانتظار البيانات</h3>
      </div>
    </div>

    <p class="notice" id="notice">
      لا توجد قراءة فعلية. البيانات التجريبية متاحة للعرض فقط.
    </p>
  </section>

  <section class="section">
    <h2>هدفنا</h2>
    <p>
      تسهيل متابعة المؤشرات المرتبطة بالحديد،
      ودعم الكشف المبكر عن التغيرات المحتملة
      من خلال تقنية ذكية قابلة للارتداء.
    </p>
  </section>
</main>

<footer>
  <h2>IRON</h2>
  <p>Smart Iron Monitoring System</p>
  <small>Healthcare Innovation | 2026</small>
</footer>

<script src="script.js"></script>
</body>
</html>

Iron


const demoBtn = document.getElementById("demoBtn");

demoBtn.addEventListener("click", function () {

  // قيمة افتراضية للشرح فقط وليست قياسًا حقيقيًا
  const exampleFerritin = 24;

  document.getElementById("ferritin").textContent =
    exampleFerritin.toFixed(1);

  document.getElementById("ironStatus").textContent =
    "مثال توضيحي";

  document.getElementById("notice").textContent =
    "هذه قيمة افتراضية لأغراض العرض فقط، ولا تمثل نتيجة تحليل أو قياسًا من اللصقة.";

  document.getElementById("connectionStatus").textContent =
    "عرض تجريبي - لا يوجد اتصال فعلي بالجهاز";

});
DOCTYPE html>

<html lang="ar" dir="rtl">

<head>

  <meta charset="UTF-8">

  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>IRON | Smart Iron Monitoring</title>

  <link rel="stylesheet" href="style.css">

</head>

<body>

<header>

  <div class="brand">IRON<span>®</span></div>

  <p>Smart Iron Monitoring System</p>

</header>

<main>

  <section class="hero">

    <span class="tag">SMART HEALTHCARE TECHNOLOGY</span>

    <h1>راقب مؤشرات الحديد بذكاء</h1>

    <p>

      نظام ذكي يعتمد على لصقة جلدية مزودة بإبر دقيقة

      وحساسات لمتابعة المؤشرات المرتبطة بالحديد.

    </p>

  </section>

  <section class="section">

    <h2>مكونات نظام IRON</h2>

    <div class="components">

      <div class="component-card">

        <div class="patch">

          <div class="patch-center">IRON</div>

        </div>

        <h3>اللصقة الذكية</h3>

        <p>لصقة دائرية مزودة بإبر دقيقة وحساسات حيوية.</p>

        <span class="status">Microneedle Patch</span>

      </div>

      <div class="component-card">

        <div class="device">

          <div class="device-screen">

            <span>IRON</span>

            <div class="screen-dot"></div>

            <small>SMART DEVICE</small>

          </div>

          <div class="device-button"></div>

        </div>

        <h3>الجهاز الإلكتروني</h3>

        <p>وحدة إلكترونية لمعالجة بيانات الحساس وإرسالها للتطبيق.</p>

        <span class="status">Electronic Unit</span>

      </div>

    </div>

  </section>

  <section class="section">

    <h2>كيف يعمل النظام؟</h2>

    <div class="steps">

      <div class="step">

        <span>01</span>

        <h3>جمع العينة</h3>

        <p>تجمع الإبر الدقيقة السائل الخلالي من الجلد.</p>

      </div>

      <div class="step">

        <span>02</span>

        <h3>تحليل المؤشرات</h3>

        <p>تعمل الحساسات على تحليل المؤشرات المستهدفة.</p>

      </div>

      <div class="step">

        <span>03</span>

        <h3>نقل البيانات</h3>

        <p>يرسل الجهاز الإلكتروني البيانات إلى التطبيق.</p>

      </div>

    </div>

  </section>

  <section class="section dashboard">

    <h2>لوحة متابعة المؤشرات</h2>

    <p class="muted">نموذج توضيحي لواجهة نتائج التطبيق</p>

    <div class="connection">

      <span class="indicator"></span>

      <span id="connectionStatus">الجهاز غير متصل فعليًا</span>

    </div>

    <button id="demoBtn">عرض نموذج قراءة تجريبية</button>

    <div class="reading">

      <div>

        <p>Ferritin</p>

        <h1 id="ferritin">--</h1>

        <small>ng/mL</small>

      </div>

      <div>

        <p>Iron Indicators</p>

        <h3 id="ironStatus">بانتظار البيانات</h3>

      </div>

    </div>

    <p class="notice" id="notice">

      لا توجد قراءة فعلية. البيانات التجريبية متاحة للعرض فقط.

    </p>

  </section>

  <section class="section">

    <h2>هدفنا</h2>

    <p>

      تسهيل متابعة المؤشرات المرتبطة بالحديد،

      ودعم الكشف المبكر عن التغيرات المحتملة

      من خلال تقنية ذكية قابلة للارتداء.

    </p>

  </section>

</main>

<footer>

  <h2>IRON</h2>

  <p>Smart Iron Monitoring System</p>

  <small>Healthcare Innovation | 2026</small>

</footer>

<script src="script.js"></script>

</body>

</html>

