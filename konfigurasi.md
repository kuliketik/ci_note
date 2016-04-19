# Konfigurasi CodeIgniter

## Tutorial configurasi CI v.3.0.3
	
	a. extrack ci.zip ke localhost 
	
	`# unzip CodeIginiter*.zip /var/www` 
	
	b. `# chmod 755 -R <Ci Path>`
	
	c. [http://localhost/ci/index.php/Welcome](http://localhost/ci/index.php/Welcome)
	
	d. ubah file `ci/application/config/autoload.php`

```
$autoload['libraries'] = array('database','session','Template'); // sementara ini dulu librarinya
$autoload['helper'] = array('url','form'); // sementara ini dulu helpernya
```
	e. ubah file `<path codeigniter>/application/config/config.php`
```
$config['base_url'] = 'http://localhost/ci/';// sesuai nama folder projek
$config['index_page'] = '';// kosongkan
```

	f. ubah file > ci/application/config/database.php
	
	ubah:
	- username 
	- password
	- nama database
	- host
	
	g. buat file *Template.php* di ci/application/libraries

isinya:

```
<?php if ( ! defined('BASEPATH')) exit('No direct script access allowed');

class Template {
    
             
		var $template_data = array();
		
		function set($name, $value)
		{
			$this->template_data[$name] = $value;
		}
	
		function load($template = '', $view = '' , $view_data = array(), $return = FALSE)
		{               
			$this->CI =& get_instance();
			$this->set('contents', $this->CI->load->view($view, $view_data, TRUE));			
			return $this->CI->load->view($template, $this->template_data, $return);
		}
}

```

## Tutorial menghapus index.php dari CI


ikutin aja yg disini :  `https://github.com/gandhi-wibowo/bookmark/blob/master/note_ci`
kalo bukan linux user, pada OOT gk usah di ikutin

3. Buat tutorial penerapan Template Bootstrap ke CI
Ok, disini ane anggep tutorial yg ke 1 and ke 2 udah di kerjain !

a. donlot templatenya, ane pake adminLTE "bisa dua template
b. buat folder template di dalam folder ci
c. pastekan folder template ke dalam folder template
d. copy file index dari templatenya
e. hapus yang di anggap tidak perlu
f. untuk url dari css / js, ubah menjadi <?php echo base_url(); ?>template/dan seterusnya
g. sisipkan <?php echo $contents; ?> untuk menampilkan data yang ingin di tampilkan
example
<html>
	<head>
	<title>Codeigniter</title>
	</head>
	<body>
	<?php echo $contents; ?>
	</body>
</html>

saya harap paham !

h. copykan file sebelumnya ke dalam /ci/application/views
i. penggunaannya
$this->template->load('templateadmin','Admin/Kategori/lihat',$data);
keterangan !
templateadmin : nama file yg di buat dari urutan #2.d
Admin/Kategori/lihat : lihat adalah nama file view yang akan digunakan untuk menampilkan data dari variable $data
yang kemudian akan di tampilkan pada <?php echo $contents; ?> dari tutorial urutan #2.g
