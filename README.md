- 👋 Hi, I’m @planet87
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
planet87/planet87 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

@RequestMapping("/answer")
    @ResponseBody
    public String answer(HttpServletResponse response, HttpServletRequest request) throws Exception {
        System.out.println(DateFormatUtils.format(new Date(), "HH:mm:ss.SSS") + " Calling.Start..");
        response.addHeader("Access-Control-Allow-Origin", "*");
        String args = request.getParameter("args").replaceAll(" ", "+");
        byte[] bts = Base64.getDecoder().decode(args);
        String input = new String(bts, "UTF-8");
        System.out.println("Input:" + input);
        JSONObject jo = JSON.parseObject(input);
        String q = jo.getString("q");
        JSONArray ja = jo.getJSONArray("ql");
        List<String> lst = new ArrayList<>();
        System.out.println("QuestList:");
        for (Object j : ja) {
            lst.add(String.valueOf(j));
            System.out.println(String.valueOf(j));
        }
        System.out.println("=====================");
        String k = ShiJuAnswer.progress(q);
        System.out.println(DateFormatUtils.format(new Date(), "HH:mm:ss.SSS") + " Calling.End..");
        System.out.println("Question:" + q + ";Answer=" + k);
        return k;
    }
