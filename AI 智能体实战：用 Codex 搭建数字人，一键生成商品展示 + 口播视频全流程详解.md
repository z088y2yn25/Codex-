# AI 智能体实战：用 Codex 搭建数字人，一键生成商品展示 + 口播视频全流程详解
短视频电商时代，商品展示视频、产品口播介绍已经成为店铺获客的核心素材。传统制作方式需要文案撰写、真人出镜、拍摄、后期剪辑，整套流程耗时久、成本高，还需要反复调整脚本。而借助 Codex AI 智能体，我们可以搭建一套自动化工作流，自动生成商品介绍脚本，驱动数字人完成商品口播与产品展示视频渲染，大幅降低短视频制作门槛。本文从原理、环境搭建、流程配置到落地调试，完整拆解这套数字人商品视频制作方案。

## 一、方案核心思路：Codex 智能体在数字人视频中的作用
很多人对 Codex 的认知还停留在代码生成工具，但在智能体架构下，Codex 可以作为**任务规划与内容生成核心**，串联起商品信息解析、口播脚本撰写、视频参数配置、数字人调度等多个环节，形成端到端的自动化流水线。

整套智能体的核心逻辑：
1. 输入商品资料（产品图、参数、卖点、目标受众）；
2. Codex 智能体读取商品信息，自主规划任务，生成适配短视频节奏的口播文案；
3. 智能体调用数字人引擎，选择人物形象、调整语速、表情、镜头；
4. 自动合成商品素材画面+数字人实时口播，输出成品商品展示视频；
5. 支持迭代优化：根据反馈修改脚本、切换数字人形象，重新渲染视频。

和单纯的文本生成模型不同，Codex 智能体具备多步骤任务编排能力，可以把“写文案、配画面、控制数字人、输出视频”拆成多个子任务自动执行，不需要人工在多个平台之间来回复制粘贴，真正实现**一键生成**。

## 二、前期准备：搭建运行环境与素材
在启动智能体之前，我们需要准备好基础组件与素材，分为三大块：
1. **Codex 智能体服务**：配置好调用入口，设置提示词模板，定义任务执行规则，让智能体知道商品视频的输出规范（时长、口播风格、卖点优先级）。
2. **数字人渲染引擎**：负责数字人形象管理、唇形同步、表情驱动、画面合成。接收智能体输出的脚本、音频参数，完成视频渲染。
3. **商品素材库**：商品主图、细节图、产品参数、核心卖点、适用场景，作为智能体生成口播文案的原始输入。

> 小提示：素材信息越完整，智能体输出的口播内容越贴合商品。只上传一张产品图，生成的文案容易空洞；补充目标人群、使用场景、对比优势，口播带货效果会明显提升。

## 三、全流程实战操作
### 步骤1：定义智能体任务，输入商品信息
把商品资料一次性喂给 Codex 智能体，同时下发任务指令：生成一段30~60秒电商短视频口播稿，突出产品核心卖点，语言口语化，节奏适合短视频，同时附带画面提示（什么时候切商品特写、什么时候展示细节）。

Codex 智能体会自动解析商品信息，完成内容规划：
- 开头钩子：快速抓住用户注意力；
- 主体部分：依次介绍产品功能、材质、优势；
- 结尾引导：添加种草、引导点击的话术；
- 同步输出画面分镜建议，用于搭配商品图片。

### 步骤2：智能体输出结构化脚本，同步生成音频指令
Codex 不只是输出纯文本文案，还会输出结构化数据：口播文本、推荐音色、语速、停顿标记、情绪标签。这些结构化数据可以直接传给数字人引擎，实现唇形和语音精准对齐。

这一步是整套方案的关键。普通大模型只能输出纯文字，需要人工二次整理；而 Codex 智能体可以按约定格式输出机器可读的脚本，实现自动化对接，省去人工复制、调整标记的工作。

### 步骤3：调度数字人，合成商品展示画面+口播
智能体将结构化脚本推送至数字人引擎后，引擎自动完成：
1. 文本转语音，生成对应音色的口播音频；
2. 根据音频驱动数字人唇形、面部微表情；
3. 按照脚本附带的分镜提示，插入商品图片、细节特写；
4. 自动剪辑拼接，生成完整商品展示视频。

你只需要选择数字人形象，全程无需手动剪辑。如果不满意效果，可以直接向 Codex 智能体下达修改指令：“文案缩短10秒，重点强调性价比，更换沉稳风格数字人”，智能体会自动重新生成脚本并触发二次渲染。

### 步骤4：视频导出与迭代优化
渲染完成后，直接导出 MP4 短视频，可直接用于抖音、视频号、小红书商品种草。
还可以建立反馈闭环：把视频观看、转化数据反馈给 Codex 智能体，让智能体持续优化文案风格，迭代出转化率更高的口播版本。

## 四、实战踩坑与优化技巧
1. **口播文案过于书面化**
    在智能体的系统提示词里强制约束：使用口语化表达，禁止长句，每句话控制在15字以内，适配短视频观看习惯。
2. **数字人唇形不同步**
    要求 Codex 智能体在脚本中增加停顿标记，把长句子切分成短句，降低音频与唇形同步的压力。
3. **商品画面和口播内容脱节**
    让智能体在输出脚本时，同步附带时间轴对应的画面指令，口播讲到哪个卖点，就展示对应的商品细节图。
4. **批量制作效率低**
    可以扩展 Codex 智能体，接入商品表格，批量读取多款商品信息，一次性批量生成多款数字人带货视频，适合多SKU店铺。

## 五、应用场景与价值总结
这套基于 Codex AI 智能体搭建的数字人视频方案，非常适合电商商家、短视频创作者、品牌运营团队：
- 电商店铺：批量制作商品种草视频、详情介绍短视频；
- 自媒体：产品测评、工具介绍类口播视频快速产出；
- 品牌宣传：新品宣讲、产品科普短视频。

核心价值在于把原来“多人协作、多软件切换”的视频制作链路，交给 AI 智能体自动化完成。只需要提供商品基础信息，就能一键输出带数字人口播的商品展示视频，大幅压缩内容制作成本，快速扩充短视频素材量。

随着智能体能力持续升级，未来还可以扩展更多能力：自动A/B测试多版口播脚本、根据用户评论自动修改视频文案、多语种跨境商品数字人视频生成。数字人内容生产，正在从“手动制作”走向由AI智能体驱动的自动化时代。

## 结尾
如果你也想低成本批量制作商品短视频，不妨尝试搭建这套 Codex 智能体+数字人工作流。先从单个商品做小范围测试，打磨提示词与工作流，再扩展到批量生产，用AI智能体释放短视频内容生产力。




https://vr.justeasy.cn/view/17922328fz15i5a8-1792328170.html
https://vr.justeasy.cn/view/17509ta423282n10-1792328221.html
https://vr.justeasy.cn/view/173y9q23k282f5l2-1792328263.html
https://vr.justeasy.cn/view/gg197o926i328292-1792328304.html
https://vr.justeasy.cn/view/1n7d9ss2328334h4-1792328345.html
https://vr.justeasy.cn/view/d41u792m3287t375-1792328386.html
https://vr.justeasy.cn/view/qn1r47v92k328416-1792328427.html
https://vr.justeasy.cn/view/017923h28t45wrw8-1792328469.html
https://vr.justeasy.cn/view/sg17759v232849t9-1792328510.html
https://vr.justeasy.cn/view/179232si68i54kj0-1792328551.html
https://vr.justeasy.cn/view/1q7c9a2n32u8f582-1792328593.html
https://vr.justeasy.cn/view/179vb1123n2862b3-1792328634.html
https://vr.justeasy.cn/view/01792w3m2f186664-1792328676.html
https://vr.justeasy.cn/view/17392z3281e706t6-1792328717.html
https://vr.justeasy.cn/view/e1729232h87rbx47-1792328759.html
https://vr.justeasy.cn/view/b17gu923mb128789-1792328800.html
https://vr.justeasy.cn/view/1yorl79232v88k31-1792328842.html
https://vr.justeasy.cn/view/179g2328gn8ss872-1792328883.html
https://vr.justeasy.cn/view/17w92328h9je1k04-1792328925.html
https://vr.justeasy.cn/view/g17d9r23288g95q5-1792328966.html
https://vr.justeasy.cn/view/17rop9w232889w96-1792329008.html
https://vr.justeasy.cn/view/1792l32i76x903r8-1792329049.html
https://vr.justeasy.cn/view/h17092xw32mf9079-1792329090.html
https://vr.justeasy.cn/view/18bi729123291d20-1792329131.html
https://vr.justeasy.cn/view/1q79ka623j29c162-1792329173.html
https://vr.justeasy.cn/view/1792i3yw29201om3-1792329214.html
https://vr.justeasy.cn/view/l1t7dz692i329244-1792329255.html
https://vr.justeasy.cn/view/1k7z9g42329uj286-1792329297.html
https://vr.justeasy.cn/view/1797i23o29zn7327-1792329338.html
https://vr.justeasy.cn/view/ou1m7y9232979368-1792329379.html
https://vr.justeasy.cn/view/1792ga31g2yv9409-1792329420.html
https://vr.justeasy.cn/view/21z79232j9k24551-1792329462.html
https://vr.justeasy.cn/view/c31792329q439xd2-1792329503.html
https://vr.justeasy.cn/view/1t79t293llf29534-1792329545.html
https://vr.justeasy.cn/view/12f792zlg32957d5-1792329587.html
https://vr.justeasy.cn/view/17923n2i96l51ol7-1792329628.html
https://vr.justeasy.cn/view/16772928m3296r58-1792329670.html
https://vr.justeasy.cn/view/fb17932c32979500-1792329711.html
https://vr.justeasy.cn/view/1o7924n3f2974hb1-1792329753.html
https://vr.justeasy.cn/view/b179232812897q83-1792329795.html
https://vr.justeasy.cn/view/q147om9232a98l25-1792329836.html
https://vr.justeasy.cn/view/13d792372998wr67-1792329878.html
https://vr.justeasy.cn/view/s17b4i9623299d08-1792329919.html
https://vr.justeasy.cn/view/s17902b3pj299q49-1792329961.html
https://vr.justeasy.cn/view/31792e3ph308x742-1792330855.html
https://vr.justeasy.cn/view/1h79b23j3i0yw884-1792330894.html
https://vr.justeasy.cn/view/61n7nu9233ss0923-1792330933.html
https://vr.justeasy.cn/view/179h2j43360963o2-1792330973.html
https://vr.justeasy.cn/view/147d492f13310031-1792331012.html
https://vr.justeasy.cn/view/h17f923jg3a10t40-1792331051.html
https://vr.justeasy.cn/view/p17v952w331q0f80-1792331090.html
https://vr.justeasy.cn/view/179w127331pe11c9-1792331130.html
https://vr.justeasy.cn/view/13gk7n923311k5a9-1792331169.html
https://vr.justeasy.cn/view/1w79ya233s11v9g8-1792331208.html
https://vr.justeasy.cn/view/y1b79e2q3i312r37-1792331248.html
https://vr.justeasy.cn/view/4i17k925331127l6-1792331287.html
https://vr.justeasy.cn/view/b1f7p92z33134x15-1792331326.html
https://vr.justeasy.cn/view/fw1779h2331rp355-1792331365.html
https://vr.justeasy.cn/view/3z17r9233b19f3t9-1792331951.html
https://vr.justeasy.cn/view/a1rct79y23312980-1792331991.html
https://vr.justeasy.cn/view/16q792332t60pt20-1792332031.html
https://vr.justeasy.cn/view/t1792363r2y0t640-1792332071.html
https://vr.justeasy.cn/view/17923i3e2pt10540-1792332110.html
https://vr.justeasy.cn/view/1k7c9233219eq739-1792332149.html
https://vr.justeasy.cn/view/a157cg92233217n8-1792332189.html
https://vr.justeasy.cn/view/u1d86796d2332217-1792332228.html
https://vr.justeasy.cn/view/5147c9a23k326295-1792332305.html
https://vr.justeasy.cn/view/tr1x7n92gk332336-1792332347.html
https://vr.justeasy.cn/view/179e9233rdzb2378-1792332390.html
https://vr.justeasy.cn/view/1792eet3p3214d21-1792332433.html
https://vr.justeasy.cn/view/1792g3k32v84ur64-1792332475.html
https://vr.justeasy.cn/view/21e792wnd3o32506-1792332518.html
https://vr.justeasy.cn/view/17923d32pp5j4xb9-1792332561.html
https://vr.justeasy.cn/view/41792f033dx22592-1792332603.html
https://vr.justeasy.cn/view/11x9799923329635-1792332646.html
https://vr.justeasy.cn/view/167q692m3326lk77-1792332689.html
https://vr.justeasy.cn/view/cy1g792m332i7120-1792332731.html
https://vr.justeasy.cn/view/171w9237p30s2762-1792332774.html
https://vr.justeasy.cn/view/e217923328ad7095-1792332817.html
https://vr.justeasy.cn/view/17x92vyz33328u47-1792332859.html
https://vr.justeasy.cn/view/o1mf79263p3u2890-1792332902.html
https://vr.justeasy.cn/view/k1j79k2lse332933-1792332944.html
https://vr.justeasy.cn/view/e17z3923yn32q975-1792332987.html
https://vr.justeasy.cn/view/c1d7x92339i301d8-1792333030.html
https://vr.justeasy.cn/view/lj1792ys33a30361-1792333072.html
https://vr.justeasy.cn/view/171792333ix10zn3-1792333115.html
https://vr.justeasy.cn/view/1xb799o263d33146-1792333158.html
https://vr.justeasy.cn/view/t1w7e9oh2333k189-1792333200.html
https://vr.justeasy.cn/view/317f9h23n353r231-1792333243.html
https://vr.justeasy.cn/view/1h70j923s0332k74-1792333285.html
https://vr.justeasy.cn/view/17ox56792333j316-1792333328.html
https://vr.justeasy.cn/view/1792o3z3q3y3dv59-1792333370.html
https://vr.justeasy.cn/view/x1s7ob923k3p3401-1792333413.html
https://vr.justeasy.cn/view/1zzg79233344ama4-1792333455.html
https://vr.justeasy.cn/view/177bj92v33348qh7-1792333498.html
https://vr.justeasy.cn/view/1p7kkm92t33352v9-1792333541.html
https://vr.justeasy.cn/view/1l179e2383ph3572-1792333583.html
https://vr.justeasy.cn/view/1hwk7lf923336u14-1792333626.html
https://vr.justeasy.cn/view/17992c3q3364yn57-1792333669.html
https://vr.justeasy.cn/view/u17ng9gv2333b700-1792333711.html
https://vr.justeasy.cn/view/179323t6337nm342-1792333754.html
https://vr.justeasy.cn/view/4fg1u79293337a85-1792333797.html
https://vr.justeasy.cn/view/179253393q73q828-1792333839.html
https://vr.justeasy.cn/view/en179cy233387080-1792333882.html
https://vr.justeasy.cn/view/1779f2u333i9a1z3-1792333925.html
https://vr.justeasy.cn/view/17l920p33qr39856-1792333968.html
https://vr.justeasy.cn/view/1739233s3h9bjw98-1792334010.html
https://vr.justeasy.cn/view/17a9p233e4fc0x41-1792334053.html
https://vr.justeasy.cn/view/1792k33340h6s8d4-1792334096.html
https://vr.justeasy.cn/view/1m7a91m432334127-1792334138.html
https://vr.justeasy.cn/view/0b17923f3o4w17w0-1792334181.html
https://vr.justeasy.cn/view/t17i29923cb34212-1792334224.html
https://vr.justeasy.cn/view/bb17e92936342j55-1792334266.html
https://vr.justeasy.cn/view/179sb123tu342948-1792334309.html
https://vr.justeasy.cn/view/718u7923v3w43490-1792334352.html
https://vr.justeasy.cn/view/179233o6o4ix4383-1792334395.html
https://vr.justeasy.cn/view/17p9v248333442g6-1792334438.html
https://vr.justeasy.cn/view/17nk492ul334q988-1792335000.html
https://vr.justeasy.cn/view/w13l792u0335t031-1792335043.html
https://vr.justeasy.cn/view/17em8p9238350274-1792335086.html
https://vr.justeasy.cn/view/17792d3352w0s117-1792335128.html
https://vr.justeasy.cn/view/17ls9l23o345n160-1792335172.html
https://vr.justeasy.cn/view/173fm9p24b335203-1792335215.html
https://vr.justeasy.cn/view/sv179i23s35qb246-1792335257.html
https://vr.justeasy.cn/view/1789rg233ji528x8-1792335300.html
https://vr.justeasy.cn/view/17al9uh23u356331-1792335343.html
https://vr.justeasy.cn/view/jt179826335737r4-1792335385.html
https://vr.justeasy.cn/view/10k7962335ia4176-1792335428.html
https://vr.justeasy.cn/view/617962335u545t69-1792335471.html
https://vr.justeasy.cn/view/n17xs925u3365502-1792335514.html
https://vr.justeasy.cn/view/179r23sok35o5445-1792335556.html
https://vr.justeasy.cn/view/6179j2335585umk8-1792335599.html
https://vr.justeasy.cn/view/187vw92py3356v31-1792335642.html
https://vr.justeasy.cn/view/17d9f2z335e6n474-1792335685.html
https://vr.justeasy.cn/view/q1wm792343m25717-1792335729.html
https://vr.justeasy.cn/view/15792733k35576i0-1792335772.html
https://vr.justeasy.cn/view/179323j35fc8nv03-1792335815.html
https://vr.justeasy.cn/view/1d79wc5723358436-1792335858.html
https://vr.justeasy.cn/view/179zg23p35a8c829-1792335900.html
https://vr.justeasy.cn/view/12kf77592w335932-1792335943.html
https://vr.justeasy.cn/view/ed8010w792335975-1792335986.html
https://vr.justeasy.cn/view/1792336u03b9r1r8-1792336029.html
https://vr.justeasy.cn/view/1791c2e33606lj60-1792336072.html
https://vr.justeasy.cn/view/6179o23k3q6h10q4-1792336115.html
https://vr.justeasy.cn/view/s179frnl233s6146-1792336158.html
https://vr.justeasy.cn/view/17nl9x9231361809-1792336201.html
https://vr.justeasy.cn/view/1l792zf3362xk342-1792336243.html
https://vr.justeasy.cn/view/17922233s0622h75-1792336286.html
https://vr.justeasy.cn/view/1792n2v3ao367318-1792336329.html
https://vr.justeasy.cn/view/179k2336o1366wj1-1792336375.html
https://vr.justeasy.cn/view/1z7b9p6j233640r6-1792336418.html
https://vr.justeasy.cn/view/12az792zo3364i49-1792336460.html
https://vr.justeasy.cn/view/b179zt323364j9g1-1792336503.html
https://vr.justeasy.cn/view/u61m799236j36534-1792336546.html
https://vr.justeasy.cn/view/l1792g3v36d657d7-1792336589.html
https://vr.justeasy.cn/view/17d92393yy6p62z0-1792336632.html
https://vr.justeasy.cn/view/179i21131e366w63-1792336675.html
https://vr.justeasy.cn/view/1792w3s93670dzv6-1792336718.html
https://vr.justeasy.cn/view/11h679x233a6x749-1792336761.html
https://vr.justeasy.cn/view/1y70e92d3ov36792-1792336807.html
https://vr.justeasy.cn/view/1d79o81233683nk9-1792336850.html
https://vr.justeasy.cn/view/17925m3cy1368x81-1792336893.html
https://vr.justeasy.cn/view/17is9v2t3386k925-1792336936.html
https://vr.justeasy.cn/view/e1j79n2336uk9768-1792336979.html
https://vr.justeasy.cn/view/17t9eo223370ch11-1792337022.html
https://vr.justeasy.cn/view/s147r9233u370254-1792337066.html
https://vr.justeasy.cn/view/1t79lg3w23637097-1792337108.html
https://vr.justeasy.cn/view/u17gp92ta3337140-1792337151.html
https://vr.justeasy.cn/view/hvv17r923037o183-1792337194.html
https://vr.justeasy.cn/view/1737r92n33s722y5-1792337237.html
https://vr.justeasy.cn/view/1d792qa337y3y268-1792337280.html
https://vr.justeasy.cn/view/17g92q337yoiv311-1792337323.html
https://vr.justeasy.cn/view/17pg9tr9233c7354-1792337366.html
https://vr.justeasy.cn/view/a1h79q2j33s73p98-1792337409.html
https://vr.justeasy.cn/view/1t79h23y037fe441-1792337453.html
https://vr.justeasy.cn/view/1m7tg923378zn484-1792337496.html
https://vr.justeasy.cn/view/417923i737d5dn28-1792337539.html
https://vr.justeasy.cn/view/b107p92367d39791-1792339805.html
https://vr.justeasy.cn/view/17923398zrnsle36-1792339848.html
https://vr.justeasy.cn/view/19s7923l39857889-1792339891.html
https://vr.justeasy.cn/view/csb178l9233996e6-1792339978.html
https://vr.justeasy.cn/view/k1679u3234800f09-1792340021.html
https://vr.justeasy.cn/view/6d17o91923400o52-1792340064.html
https://vr.justeasy.cn/view/1379h234arny0095-1792340107.html
https://vr.justeasy.cn/view/17a9b2340fc13xr8-1792340150.html
https://vr.justeasy.cn/view/18w979p23s400182-1792340193.html
https://vr.justeasy.cn/view/0967179k23402n25-1792340236.html
https://vr.justeasy.cn/view/xw1vr792w34p0268-1792340280.html
https://vr.justeasy.cn/view/1792th73j4t20312-1792340323.html
https://vr.justeasy.cn/view/1y7c96234pvf0355-1792340366.html
https://vr.justeasy.cn/view/17928h3k4gi20398-1792340410.html
https://vr.justeasy.cn/view/ev1792q3410k44e1-1792340453.html
https://vr.justeasy.cn/view/179ns2j340u4i8o4-1792340496.html
https://vr.justeasy.cn/view/x17r92c3x40v5a27-1792340539.html
https://vr.justeasy.cn/view/s1hm7jz923401571-1792340582.html
https://vr.justeasy.cn/view/17923mk4ze061613-1792340625.html
https://vr.justeasy.cn/view/17q992gl34065y16-1792340668.html
https://vr.justeasy.cn/view/k9517s927m340699-1792340711.html
https://vr.justeasy.cn/view/17y9q23qgl4074d2-1792340754.html
https://vr.justeasy.cn/view/u179234n0974wl85-1792340797.html
https://vr.justeasy.cn/view/pb1q7c692340w828-1792340840.html
https://vr.justeasy.cn/view/17y92345087dd1h2-1792340883.html
https://vr.justeasy.cn/view/1791234w0091k7a5-1792340926.html
https://vr.justeasy.cn/view/t179y234m007o957-1792340969.html
https://vr.justeasy.cn/view/187698234810r0x0-1792341012.html
https://vr.justeasy.cn/view/179o23441u0rc4e3-1792341055.html
https://vr.justeasy.cn/view/1792v34x10w8tek6-1792341098.html
https://vr.justeasy.cn/view/xq17o9234f119259-1792341141.html
https://vr.justeasy.cn/view/17v92341oe631723-1792341184.html
https://vr.justeasy.cn/view/b1739n2384w1w215-1792341227.html
https://vr.justeasy.cn/view/1732923sp41p2258-1792341270.html
https://vr.justeasy.cn/view/1z71z923g4s13a01-1792341312.html
https://vr.justeasy.cn/view/18j792cve3413404-1792341355.html
https://vr.justeasy.cn/view/c1g792n341t3y8j7-1792341398.html
https://vr.justeasy.cn/view/n17y92t3r4143lf0-1792341441.html
https://vr.justeasy.cn/view/17y79232s414g7n3-1792341485.html
https://vr.justeasy.cn/view/3179234beszh1516-1792341528.html
https://vr.justeasy.cn/view/4179v2c3410u5760-1792341571.html
https://vr.justeasy.cn/view/917923t34169hq02-1792341617.html
https://vr.justeasy.cn/view/1769y2d3z4c16148-1792341659.html
https://vr.justeasy.cn/view/v1m79234t8117691-1792341702.html
https://vr.justeasy.cn/view/k17h92j6d34d1734-1792341745.html
https://vr.justeasy.cn/view/1879236s6417t7l8-1792341788.html
https://vr.justeasy.cn/view/1y719k23s4418220-1792341831.html
https://vr.justeasy.cn/view/481p79q23n4186z3-1792341874.html
https://vr.justeasy.cn/view/x1799234o519h026-1792341917.html
https://vr.justeasy.cn/view/170u92b341gk9499-1792341961.html
https://vr.justeasy.cn/view/17902ik3419uyc93-1792342004.html
https://vr.justeasy.cn/view/17972363442dq036-1792342048.html
https://vr.justeasy.cn/view/11p7u92342g08680-1792342091.html
https://vr.justeasy.cn/view/1s579ce2m3w42123-1792342134.html
https://vr.justeasy.cn/view/17ph923l4216ypn6-1792342177.html
https://vr.justeasy.cn/view/1791f2342520rmc8-1792342220.html
https://vr.justeasy.cn/view/1792344u22m597d1-1792342262.html
https://vr.justeasy.cn/view/17k9z23425ga2z94-1792342306.html
https://vr.justeasy.cn/view/e1v7923f4x239328-1792342349.html
https://vr.justeasy.cn/view/14w7923423j43981-1792342393.html
https://pastebin.com/wCvcnDQW
https://pastebin.com/RdTuczZk
https://pastebin.com/kA8xYwga
https://pastebin.com/NJyGQF1V
https://pastebin.com/ckktAEQg
https://pastebin.com/WKtsnxNV
https://pastebin.com/UJ4bEFi9
https://pastebin.com/MCVCSFHC
https://pastebin.com/DhWfEmtT
https://pastebin.com/R0c3pRwt
https://pastebin.com/t6DzGZer
https://pastebin.com/15JBXWwa
https://pastebin.com/Q244hJvC
https://pastebin.com/E0GChEs7
https://pastebin.com/TZ5fWgBS
https://pastebin.com/J4Vm2NV4
https://pastebin.com/kLkXYA9t
https://pastebin.com/vb9wn5Yd
https://pastebin.com/w9EGiQGC
https://pastebin.com/zd7LWPYq
https://pastebin.com/TpaX7ATB
https://pastebin.com/k3MbrmM3
https://pastebin.com/E8cMZn9c
https://pastebin.com/uQKXmMbL
https://pastebin.com/YAfsYXpi
https://pastebin.com/ifSF2XtP
https://pastebin.com/66c4NNhw
https://pastebin.com/7NUzqkRt
https://pastebin.com/Rgk0r3AQ
https://pastebin.com/AiTTQvH2
https://pastebin.com/t5q1nxWy
https://pastebin.com/P6kkpH5p
https://pastebin.com/7gHwxjF4
https://pastebin.com/aGK2e3mc
https://pastebin.com/069ve3X2
https://pastebin.com/JjN8EchA
https://pastebin.com/Z76SU9fr
https://pastebin.com/hEFqN9em
https://pastebin.com/hEWqZUnF
https://pastebin.com/3AqwfZ3R
https://pastebin.com/anb8ufYb
https://pastebin.com/Av4xpfmy
https://pastebin.com/a74X0Qyv
https://pastebin.com/ZS9vmxqY
https://pastebin.com/533TFwSe
https://pastebin.com/KTmBsivr
https://pastebin.com/urxHhr3v
https://pastebin.com/Z7M8BYRn
https://pastebin.com/7xQFLzr7
https://pastebin.com/c4w0E82s
https://pastebin.com/c7Mbatnq
https://pastebin.com/KYTxjiat
https://pastebin.com/Hjhzk208
https://pastebin.com/rMtUezuA
https://pastebin.com/FvdNNbNP
https://pastebin.com/FrxX4B3z
https://pastebin.com/5qTbBxX3
https://pastebin.com/UKRvbC0C
https://pastebin.com/w7CsUTzw
https://pastebin.com/Kx2jcrdu
https://pastebin.com/ZZDrhaCJ
https://pastebin.com/W6UquUfN
https://pastebin.com/LEeaDhc7
https://pastebin.com/nckKP8uc
https://pastebin.com/NQh10U6t
https://pastebin.com/d2cbCf6H
https://pastebin.com/EVyEdiN4
https://pastebin.com/872GUsy0
https://pastebin.com/j57Bkx5F
https://pastebin.com/TPSVmVUq
https://pastebin.com/3CNaR01M
https://pastebin.com/xuhFM57e
https://pastebin.com/BMF3Cx2d
https://pastebin.com/xMgctPst
https://pastebin.com/H76uF4jS
https://pastebin.com/JMkrbV7s
https://pastebin.com/pBmhmh6P
https://pastebin.com/SEvGBfSQ
https://pastebin.com/zd7LWPYq
https://pastebin.com/TpaX7ATB
https://pastebin.com/k3MbrmM3
https://pastebin.com/E8cMZn9c
https://pastebin.com/uQKXmMbL
https://pastebin.com/YAfsYXpi
https://pastebin.com/ifSF2XtP
https://pastebin.com/66c4NNhw
https://pastebin.com/7NUzqkRt
https://pastebin.com/Rgk0r3AQ
https://pastebin.com/AiTTQvH2
https://pastebin.com/t5q1nxWy
https://pastebin.com/P6kkpH5p
https://pastebin.com/7gHwxjF4
https://pastebin.com/aGK2e3mc
https://pastebin.com/069ve3X2
https://pastebin.com/JjN8EchA
https://pastebin.com/Z76SU9fr
https://pastebin.com/hEFqN9em
https://pastebin.com/hEWqZUnF
https://pastebin.com/3AqwfZ3R
https://pastebin.com/anb8ufYb
https://pastebin.com/Av4xpfmy
https://pastebin.com/a74X0Qyv
https://pastebin.com/ZS9vmxqY
https://pastebin.com/533TFwSe
https://pastebin.com/KTmBsivr
https://pastebin.com/urxHhr3v
https://pastebin.com/Z7M8BYRn
https://pastebin.com/7xQFLzr7
https://pastebin.com/c4w0E82s
https://pastebin.com/c7Mbatnq
https://pastebin.com/KYTxjiat
https://pastebin.com/Hjhzk208
https://pastebin.com/rMtUezuA
https://pastebin.com/FvdNNbNP
https://pastebin.com/FrxX4B3z
https://pastebin.com/5qTbBxX3
https://pastebin.com/UKRvbC0C
https://pastebin.com/w7CsUTzw
https://pastebin.com/Kx2jcrdu
https://pastebin.com/ZZDrhaCJ
https://pastebin.com/W6UquUfN
https://pastebin.com/LEeaDhc7
https://pastebin.com/nckKP8uc
https://pastebin.com/NQh10U6t
https://pastebin.com/d2cbCf6H
https://pastebin.com/EVyEdiN4
https://pastebin.com/872GUsy0
https://pastebin.com/j57Bkx5F
https://pastebin.com/TPSVmVUq
https://pastebin.com/3CNaR01M
https://pastebin.com/xuhFM57e
https://pastebin.com/BMF3Cx2d
https://pastebin.com/xMgctPst
https://pastebin.com/H76uF4jS
https://pastebin.com/JMkrbV7s
https://pastebin.com/pBmhmh6P
https://pastebin.com/SEvGBfSQ
https://www.720yuntu.com/author?pk=131480
https://www.720yuntu.com/tour/17f096ff4e2dfa13
https://www.720yuntu.com/author?pk=131481
https://www.720yuntu.com/author?pk=131482
https://www.720yuntu.com/author?pk=131483
https://www.720yuntu.com/author?pk=131484
https://www.720yuntu.com/author?pk=131485
https://www.720yuntu.com/author?pk=131486
https://www.720yuntu.com/author?pk=131487
https://www.720yuntu.com/tour/6547e5a9cae2341e
https://www.720yuntu.com/tour/54f262c723e114e4
https://www.720yuntu.com/tour/db8cb93837489b0d
https://www.720yuntu.com/tour/6eabc5db065b80b9
https://www.720yuntu.com/tour/a0c037fe892931dd
https://www.720yuntu.com/tour/d2137c57667e4696
https://www.720yuntu.com/tour/2cdf0341ba5ffd26
https://www.720yuntu.com/tour/9591ee2b92fba140
https://www.720yuntu.com/tour/bcefca69e52a72b0
https://www.720yuntu.com/tour/8ebe710a7071e229
https://www.720yuntu.com/tour/ec833d23f82d7756
https://www.720yuntu.com/tour/d89f3c0d5dfa094c
https://www.720yuntu.com/tour/646e24a8e844b196
https://www.720yuntu.com/tour/9ae3dc99b3fabc1b
https://www.720yuntu.com/tour/921db251fda8a1ae
https://www.720yuntu.com/tour/8031641d5754b253
https://www.720yuntu.com/tour/b577dd621abd2785
https://www.720yuntu.com/tour/86cd50b0663d9e9d
https://www.720yuntu.com/tour/b43184e9aca29d99
https://www.720yuntu.com/tour/61d7b94154e52309
https://www.720yuntu.com/tour/bb7c8871643ee670
https://www.720yuntu.com/tour/c0f49ef84eacaf99
https://www.720yuntu.com/tour/335956c7209cc1fb
https://www.720yuntu.com/tour/9f3ccddfbf99e771
https://www.720yuntu.com/tour/7d89f8a97546a196
https://www.720yuntu.com/tour/e37bfea7a8b2cd54
https://www.720yuntu.com/tour/34f816ad195633b7
https://www.720yuntu.com/tour/2794358c5a0a3371
https://www.720yuntu.com/tour/357e70c224a1e8fc
https://www.720yuntu.com/tour/51b16645aca9c956
https://www.720yuntu.com/tour/4115b5b7ea690ce9
https://www.720yuntu.com/tour/82dc0f8a94bb6143
https://www.720yuntu.com/tour/f43dd9fefef980de
https://www.720yuntu.com/tour/baff8c0d847d64bf
https://www.720yuntu.com/tour/fb30c0f942424200
https://www.720yuntu.com/tour/70ab8ba4ebf08f3c
https://www.720yuntu.com/tour/066e30d2a9ac7e77
https://www.720yuntu.com/tour/1830722333d4a281
https://www.720yuntu.com/tour/8e971d99ec607cfd
https://www.720yuntu.com/tour/6d83f67185df1d4d
https://www.720yuntu.com/tour/b172664f9aea3a8d
https://www.720yuntu.com/tour/59a07ac3381fe8c4
https://www.720yuntu.com/tour/a86e0db7961439ec
https://www.720yuntu.com/tour/87e77eb2d6862557
https://www.720yuntu.com/tour/2fee7dc624d5e34e
https://www.720yuntu.com/tour/6869849d6f935199
https://www.720yuntu.com/tour/c13d9ce8eec04cf6
https://www.720yuntu.com/tour/ab91c16706370bf8
https://www.720yuntu.com/tour/04c297f540a72e0f
https://www.720yuntu.com/tour/c7025c08f30b4f64
https://www.720yuntu.com/tour/f008976a45d04749
https://www.720yuntu.com/tour/414a92a397868909
https://www.720yuntu.com/tour/3f203e03d66764e1
https://www.720yuntu.com/tour/e178b7e61f970eaf
https://www.720yuntu.com/tour/8df66efaa8664aaa
https://www.720yuntu.com/tour/c8d9498970d1c1fb
https://www.720yuntu.com/tour/bbfeca36e4eed5a3
https://www.720yuntu.com/tour/0f127662e67bee7d
https://www.720yuntu.com/tour/3770054508818729
https://www.720yuntu.com/tour/78cabb09274eba7b
https://www.720yuntu.com/tour/c9796ff9c044272b
https://www.720yuntu.com/tour/ee39927983db6c20
https://www.720yuntu.com/tour/b5c7060c9493d1ca
https://www.720yuntu.com/tour/4f71dbf7f99e1c98
https://www.720yuntu.com/tour/f77cb6c799f52b91
https://www.720yuntu.com/tour/b3280895d630d0b9
https://www.720yuntu.com/tour/ad6abf7a579d4646
https://www.720yuntu.com/tour/8b29a505f9436a1c
https://www.720yuntu.com/tour/4892e0ab56af2031
https://www.720yuntu.com/tour/37094b9fb1eb611e
https://www.720yuntu.com/tour/fa0c6ba8d51e34c6
https://www.720yuntu.com/tour/380226e01c52004e
https://www.720yuntu.com/tour/961fca309e822468
https://www.720yuntu.com/tour/262810ef6343abdf
https://www.720yuntu.com/tour/3458226a80783060
https://www.720yuntu.com/tour/e5c0569edb0707a1
https://www.720yuntu.com/tour/d6b2ae576238e568
https://www.720yuntu.com/tour/1798d0412407705b
https://www.720yuntu.com/tour/097e92875718acb2
https://www.720yuntu.com/tour/8494a43a640eaec3
https://www.720yuntu.com/tour/ffbc0d44983465df
https://www.720yuntu.com/tour/9f67763672c3bb13
https://www.720yuntu.com/tour/180ccb3877ccbcc8
https://www.720yuntu.com/tour/d7d74de3a437ac29
https://www.720yuntu.com/tour/c81765438b5bba54
https://www.720yuntu.com/tour/3d21576be4d6cc33
https://www.720yuntu.com/tour/f5dbdb1f4ac7bc37
https://www.720yuntu.com/tour/53fcec954c1ce3e7
https://www.720yuntu.com/tour/131f205fbb14839d
https://www.720yuntu.com/tour/b9ebed666c8f48cf
https://www.720yuntu.com/tour/e90a8658cf1ab653
https://www.720yuntu.com/tour/15c8c3a13bbd9601
https://www.720yuntu.com/tour/cc36a2939e4a4971
https://www.720yuntu.com/tour/5884ffbc6aaa5f51
https://www.720yuntu.com/tour/404d4390db377ab1
https://www.720yuntu.com/tour/c861fba904160e32
https://www.720yuntu.com/tour/ec7172f0959448a7
https://www.720yuntu.com/tour/04bd98333aae4904
https://www.720yuntu.com/tour/973aa4f1114165c6
https://www.720yuntu.com/tour/e52cf5cd7fb1052c
https://www.720yuntu.com/tour/ac783ff8568bb38d
https://www.720yuntu.com/tour/a935d7de87cb9039
https://www.720yuntu.com/tour/ddf2115c2eb35af3
https://www.720yuntu.com/tour/2e6ba362d1e511cd
https://www.720yuntu.com/tour/9ed7e88d8bc00445
https://www.720yuntu.com/tour/d72bb4288389615b
https://www.720yuntu.com/tour/64a3acd7669c5767
https://www.720yuntu.com/tour/2951f1b2f73e46b9
https://www.720yuntu.com/tour/812bba5bda9b1966
https://www.720yuntu.com/tour/8258ba537fb010ad
https://www.720yuntu.com/tour/6cdfc8048e8da5b1
https://www.720yuntu.com/tour/9a8b490b34d48158
https://www.720yuntu.com/tour/077c80a30ca79d08
https://www.720yuntu.com/tour/ff612e8bfbaacf12
https://www.720yuntu.com/tour/8ef83bc46a03dcad
https://www.720yuntu.com/tour/71b894f59722254c
https://www.720yuntu.com/tour/71e4d5dca585620f
https://www.720yuntu.com/tour/e0db22f5e26458cf
https://www.720yuntu.com/tour/d9194e069bb34ee0
https://www.720yuntu.com/tour/70ba709888bd1d40
https://www.720yuntu.com/tour/5af1b93b9875eee1
https://www.720yuntu.com/tour/bfce909ccee33a97
https://www.720yuntu.com/tour/6dc38cf77d66e4a2
https://www.720yuntu.com/tour/89bd62554163ed35
https://www.720yuntu.com/tour/3e2bf087bf73780d
https://www.720yuntu.com/tour/74eac06d86f12a5b
https://www.720yuntu.com/tour/80708594bc6fb7e5
https://www.720yuntu.com/tour/9105b229f9ccd9be
https://www.720yuntu.com/tour/ba85a73fbde1fe6e
https://www.720yuntu.com/tour/2743952bc4d29e8a
https://www.720yuntu.com/tour/eafee55eb8362090
https://www.720yuntu.com/tour/68bb5182c1e50bf7
https://www.720yuntu.com/tour/ca80bc916ed08355
https://www.720yuntu.com/tour/85fb23896066e6bf
https://www.720yuntu.com/tour/ed9d12a81e94dc7e
https://www.720yuntu.com/tour/899d61abf23ae193
https://www.720yuntu.com/tour/0a1e69f69a5400f9
https://www.720yuntu.com/tour/bec44cfcea337bb2
https://www.720yuntu.com/tour/7fa819e6855d4a8c
https://www.720yuntu.com/tour/ab234bf9a5e3fe08
https://www.720yuntu.com/tour/4c6ac2af55b4fe83
https://www.720yuntu.com/tour/82d410a0f6e5d254
https://www.720yuntu.com/tour/f22e4b7be16f3f81
https://www.720yuntu.com/tour/d96dc9706962575e
https://www.720yuntu.com/tour/e6ff144074e95b5e
https://www.720yuntu.com/tour/10c3a9557a8136bd
https://www.720yuntu.com/tour/e2aba382f8580737
https://www.720yuntu.com/tour/cf86e7e4c99c5a47
https://www.720yuntu.com/tour/bd03341e6bd42d23
https://www.720yuntu.com/tour/4b96b6d7cc999c43
https://www.720yuntu.com/tour/c7e92de9b85714ef
https://www.720yuntu.com/tour/a7d92e269f4b88bc
https://www.720yuntu.com/tour/97c3cd702a71f3d0
https://www.720yuntu.com/tour/84242a4d8176d16a
https://www.720yuntu.com/tour/9acf99566fb426c1
https://www.720yuntu.com/tour/135cc185f4c21cb2
https://www.720yuntu.com/tour/da55199c09eb2e58
https://www.720yuntu.com/tour/116dbb4a61ce7eaf
https://www.720yuntu.com/tour/7481500966cb063e
https://www.720yuntu.com/tour/8852b76e7f3459f1
https://www.720yuntu.com/tour/dc363ca8e1ce2d9f
https://www.720yuntu.com/tour/83f2c2c5145f9722
https://www.720yuntu.com/tour/ae46eeea6a061abf
https://www.720yuntu.com/tour/229c4e80503939b5
https://www.720yuntu.com/tour/c4764a7b327d401e
https://www.720yuntu.com/tour/a536b76663fead8b
https://www.720yuntu.com/tour/d342098ef4f2fbf9
https://www.720yuntu.com/tour/f2e5f7562e2afbe6
https://www.720yuntu.com/tour/685c75efa76dbb1b
https://www.720yuntu.com/tour/601963e1276cfcde
https://www.720yuntu.com/tour/13e66adc4ea7c377
https://www.720yuntu.com/tour/3ad43ba2b026784a
https://www.720yuntu.com/tour/86c5296dc3e060ae
https://www.720yuntu.com/tour/d6f0644ff7d87678
https://www.720yuntu.com/tour/b75843f68ad495db
https://www.720yuntu.com/tour/6419c685c22ed8ed
https://www.720yuntu.com/tour/7c6836abf91532b9
https://www.720yuntu.com/tour/cb35e8c7c7eac610
https://www.720yuntu.com/tour/9ea748894bfcc64c
https://www.720yuntu.com/tour/b720cfa2ef7bd532
https://www.720yuntu.com/tour/eaf66505fcc6261e
https://www.720yuntu.com/tour/62a6d63a84bb3523
https://www.720yuntu.com/tour/f4e0960708814b2a
https://www.720yuntu.com/tour/8fcf4a5f221fec1a
https://www.720yuntu.com/tour/37a79e96be98ce13
https://www.720yuntu.com/tour/7a892e3273b20074
https://www.720yuntu.com/tour/5c8483952c6f2307
https://www.720yuntu.com/tour/5b3bba9222e2ab5c
https://www.720yuntu.com/tour/a7d467b33324b51b
https://www.720yuntu.com/tour/dd6a6c5a9ef6efdc
https://www.720yuntu.com/tour/f04ff32e5fe0083b
https://www.720yuntu.com/tour/a996da0bb71b626c
https://www.720yuntu.com/tour/a452f1480fc4ea36
https://www.720yuntu.com/tour/6fb1bee842a02c68
https://www.720yuntu.com/tour/77264161103bc6b6
https://www.720yuntu.com/tour/91eb1269f8a3ee5c
https://www.720yuntu.com/tour/cd7056a82c745208
https://www.720yuntu.com/tour/ac75464efcf85c26
https://www.720yuntu.com/tour/c717acdd14ba6ff0
https://www.720yuntu.com/tour/a521581c9a537395
https://www.720yuntu.com/tour/da4ecda1eb8a6272
https://www.720yuntu.com/tour/923edba24cdb5bf3
https://www.720yuntu.com/tour/a6cc3ad5c9de453f
https://www.720yuntu.com/tour/9b7283feb9c660cc
https://www.720yuntu.com/tour/2ea7984a8a51250a
https://www.720yuntu.com/tour/679bb47b368379df
https://www.720yuntu.com/tour/85fabfd88fec1f7e
https://www.720yuntu.com/tour/8ca8d9f7e820b8b0
https://www.720yuntu.com/tour/cf165b31cc126517
