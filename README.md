# Spinner-Kullan-m-
Spinner Kullanımı
String.xml

    <string name="isimler">Names :</string>
    <string name="renkler">Colors :</string>
    <string-array name="renkler">
        <item>gray</item>
        <item>blue</item>
        <item>red</item>
        <item>yellow</item>
        <item>green</item>
        <item>magenta</item>
        <item>white</item>
        <item>black</item>
    </string-array>
    <string-array name="isimler">
        <item>Ali</item>
        <item>Veli</item>
        <item>Ayşe</item>
        <item>Fatma</item>
        <item>Uygar</item>
        <item>Özgür</item>
        <item>Aykut</item>
        <item>Berkay</item>
    </string-array>
    
    class MainActivity : AppCompatActivity() {
    lateinit var spnRenkler: Spinner
    lateinit var spnIsimler:Spinner
    lateinit var ekran: ConstraintLayout
    lateinit var lvIsimler: ListView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        ekran=findViewById(R.id.ekran)
        spnIsimler=findViewById(R.id.spnIsimler)
        spnRenkler=findViewById(R.id.spnRenkler)
        lvIsimler=findViewById(R.id.lvIsimler)
        val adlar= arrayOf("Ali","Veli","Ayşe")
        val isimler=resources.getStringArray(R.array.isimler)
        val renkler=resources.getStringArray(R.array.renkler)
        val renkAdapter= ArrayAdapter<String>(this,android.R.layout.simple_list_item_1,renkler)
        spnRenkler.adapter=renkAdapter
        spnRenkler.onItemSelectedListener= object : AdapterView.OnItemSelectedListener{
            override fun onItemSelected(
                parent: AdapterView<*>?,
                view: View?,
                position: Int,
                id: Long
            ) {
                Toast.makeText(applicationContext,renkler[position].toString(),Toast.LENGTH_LONG).show()
                when(position) {
                    0 -> ekran.setBackgroundColor(Color.GRAY)
                    1 -> ekran.setBackgroundColor(Color.BLUE)
                    2 -> ekran.setBackgroundColor(Color.RED)
                    3 -> ekran.setBackgroundColor(Color.YELLOW)
                    4 -> ekran.setBackgroundColor(Color.GREEN)
                    5 -> ekran.setBackgroundColor(Color.MAGENTA)
                    6 -> ekran.setBackgroundColor(Color.WHITE)
                    7 -> ekran.setBackgroundColor(Color.BLACK)
                }
            }
            override fun onNothingSelected(parent: AdapterView<*>?) {
                TODO("Not yet implemented")
            }
        }

        val isimAdapter=ArrayAdapter<String>(this,R.layout.goruntu,isimler)
        val listeAdapter=ArrayAdapter<String>(this,R.layout.liste_goruntu,isimler)
        lvIsimler.adapter=listeAdapter
        lvIsimler.onItemClickListener=AdapterView.OnItemClickListener { parent, view, position, id ->
            Toast.makeText(applicationContext,"Seçilen : ${isimler[position]}",Toast.LENGTH_LONG).show()
        }
        spnIsimler.adapter=isimAdapter
        spnIsimler.onItemSelectedListener= object : AdapterView.OnItemSelectedListener{
            override fun onItemSelected(
                parent: AdapterView<*>?,
                view: View?,
                position: Int,
                id: Long
            ) {
                Toast.makeText(applicationContext,isimler[position].toString(),Toast.LENGTH_LONG).show()
            }
            override fun onNothingSelected(parent: AdapterView<*>?) {
            }
        }
    }
}
    

