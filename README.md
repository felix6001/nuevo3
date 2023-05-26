# nuevo3

<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:id="@+id/menu_contacto"
        android:title="Contacto" />
    <item
        android:id="@+id/menu_acerca_de"
        android:title="Acerca De" />
</menu>

override fun onCreateOptionsMenu(menu: Menu): Boolean {
    menuInflater.inflate(R.menu.menu_main, menu)
    return true
}

override fun onOptionsItemSelected(item: MenuItem): Boolean {
    when (item.itemId) {
        R.id.menu_contacto -> {
            val intent = Intent(this, ContactoActivity::class.java)
            startActivity(intent)
            return true
        }
        R.id.menu_acerca_de -> {
            val intent = Intent(this, AcercaDeActivity::class.java)
            startActivity(intent)
            return true
        }
        else -> return super.onOptionsItemSelected(item)
    }
}

class ContactoActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_contacto)
        
        // Configurar el botón de "Enviar Comentario"
        val enviarComentarioButton: Button = findViewById(R.id.enviarComentarioButton)
        enviarComentarioButton.setOnClickListener {
            // Obtener la información recopilada del formulario
            val nombre = nombreEditText.text.toString()
            val correo = correoEditText.text.toString()
            val mensaje = mensajeEditText.text.toString()
            
            // Enviar el comentario utilizando la librería JavaMail
            // (Implementación de JavaMail requerida)
        }
    }
}
class AcercaDeActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_acerca_de)
        
        // Configurar la bio del desarrollador
        // (Puedes mostrar la información en un TextView)
    }
}

<androidx.viewpager.widget.ViewPager
    android:id="@+id/viewPager"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />

class ViewPagerAdaptador(fragmentManager: FragmentManager) : FragmentPagerAdapter(fragmentManager) {

    override fun getItem(position: Int): Fragment {
        return when (position) {
            0 -> MascotaPerfilFragment()
            1 -> MascotaFotosFragment()
            else -> throw IllegalArgumentException("Posición inválida")
        }
    }

    override fun getCount(): Int {
        return 2
    }
}

Modificar la actividad principal (MainActivity) para utilizar el ViewPager:

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        
        val viewPager: ViewPager = findViewById(R.id.viewPager)
        val adapter = ViewPagerAdaptador(supportFragmentManager)
        viewPager.adapter = adapter
    }
}

Recuerda ajustar los layouts y agregar los recursos necesarios para mostrar la información y las imágenes correctamente en los fragments.
