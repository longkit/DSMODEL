public class SEIRSModel {
    public static void main(String[] args) {
        // پارامترها و شرایط اولیه
        int N = 1000; // تعداد جمعیت کل
        double I0 = 1; // تعداد افراد مبتلا اولیه
        double S0 = N - I0; // تعداد افراد حساس اولیه
        double E0 = 0; // تعداد افراد در دوره کمون اولیه
        double R0 = 0; // تعداد افراد بهبود یافته اولیه
        double beta = 0.3; // نرخ انتقال بیماری
        double sigma = 0.2; // نرخ پیشرفت از دوره کمون به دوره مبتلا
        double gamma = 0.1; // نرخ بهبود بیماری
        double delta = 0.05; // نرخ بازگشت افراد به حالت حساس پس از بهبودی

        int steps = 1000; // تعداد مراحل شبیه‌سازی
        double dt = 0.1; // گام زمانی

        // ایجاد آرایه‌ها برای ذخیره نتایج
        double[] S = new double[steps + 1];
        double[] E = new double[steps + 1];
        double[] I = new double[steps + 1];
        double[] R = new double[steps + 1];

        // مقادیر اولیه
        S[0] = S0;
        E[0] = E0;
        I[0] = I0;
        R[0] = R0;

        // اجرای شبیه‌سازی با استفاده از روش اویلر
        for (int t = 0; t < steps; t++) {
            double dS = (-beta * S[t] * I[t] / N + delta * R[t]) * dt;
            double dE = (beta * S[t] * I[t] / N - sigma * E[t]) * dt;
            double dI = (sigma * E[t] - gamma * I[t]) * dt;
            double dR = (gamma * I[t] - delta * R[t]) * dt;

            S[t + 1] = S[t] + dS;
            E[t + 1] = E[t] + dE;
            I[t + 1] = I[t] + dI;
            R[t + 1] = R[t] + dR;
        }

        // چاپ نتایج
        System.out.println("Time\tSusceptible\tExposed\tInfectious\tRecovered");
        for (int t = 0; t <= steps; t++) {
            System.out.printf("%.2f\t%.2f\t\t%.2f\t\t%.2f\t\t%.2f\n", t * dt, S[t] ,  E[t] , I[t], R[t]);
        }
    }
}
