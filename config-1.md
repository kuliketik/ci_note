1. Buat tutorial configurasi CI v.3.0.3
	
	a. extrack ci.zip ke localhost 
	`# unzip CodeIginiter*.zip /var/www 
	
	
	b. # chmod 755 -R <Ci Path>
	
	c. [http://localhost/ci/index.php/Welcome](http://localhost/ci/index.php/Welcome)
	
	d. ubah file > ci/application/config/autoload.php

```
$autoload['libraries'] = array('database','session','Template');// sementara ini dulu librarinya
$autoload['helper'] = array('url','form');// sementara ini dulu helpernya
```
	e. ubah file > ci/application/config/config.php
```
$config['base_url'] = 'http://localhost/ci/';// sesuai nama folder projek
$config['index_page'] = '';// kosongkan
```

	f. ubah file > ci/application/config/database.php
	ubah username, password, nama database, hostnya
	
	g. buat file Template.php di ci/application/libraries

isinya
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
