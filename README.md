- 👋 Hi, I’m @planet87
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
planet87/planet87 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

public class ShiJuAnswer {

    static final String[] SPLITS = new String[]{",", "，", " ", ".", "。", "!", "！", "?", "？"};


    public static String progress(String front) throws Exception {
        if (front.contains("下句是")) {
            String pre = front.substring(0, front.indexOf("下句是"));
            for (String s : SPLITS) {
                pre = pre.replace(s, "");
            }
            return nextSentence(pre);
        } else {
            return baiduType(front);
        }
    }

    private static String baiduType(String question) {
        return null;
    }

    public static String nextSentence(String front) throws Exception {
        String tplUrl = "https://so.gushiwen.cn/search.aspx?value=" + front + "&valuej=" + front.substring(0, 1);
        String rsp = HttpCall.getUrl(tplUrl, new HashMap<>(), new HashMap<>());
        rsp = rsp.substring(rsp.indexOf(front) + front.length());

        int idx = rsp.indexOf(front);
        if (idx < 0) {
            return "Failed1";
        }
        rsp = rsp.substring(idx + front.length());
        int s2 = rsp.indexOf("</textarea>");
        if (s2 < 0) {
            return "Failed2";
        }
        String content = rsp.substring(0, s2);

        String[] dvs = content.split("[,， .。!！?？]");
        for (String d : dvs) {
            if (null != d && d.trim().length() != 0 && d.trim().length() < 10) {
                return d.trim();
            }
        }
        return "Failed3";
    }
}
