# actividad7
public function up()
{
    Schema::create('usuarios', function (Blueprint $table) {
        $table->id();
        $table->string('nombre');
        $table->enum('rol', ['estudiante', 'profesor', 'administrador']);
        $table->timestamps();
    });
}

public function cursos()
{
    return $this->belongsToMany(Curso::class, 'curso_usuarios', 'usuario_id', 'curso_id')->withTimestamps();
}

public function up()
{
    Schema::create('cursos', function (Blueprint $table) {
        $table->id();
        $table->string('clave_curso');
        $table->string('nombre');
        $table->string('kit_robotica');
        $table->timestamps();
    });
}
public function usuarios()
{
    return $this->belongsToMany(Usuario::class, 'curso_usuarios', 'curso_id', 'usuario_id')->withTimestamps();
}

public function grupo()
{
    return $this->belongsTo(Grupo::class);
}

public function up()
{
    Schema::create('grupos', function (Blueprint $table) {
        $table->id();
        $table->string('nombre');
        $table->timestamps();
    });
}
public function cursos()
{
    return $this->hasMany(Curso::class);
}
