
## ��**什么是 Blade？**
```php
// Blade 是 Laravel 的模板引擎
// 文件：.blade.php
// 位置：resources/views/
```

## �� **基础语法**

### **1. 输出变量**
```php
{{ $title }}        {{-- 输出变量，自动转义 --}}
{!! $content !!}    {{-- 输出 HTML，不转义 --}}
{{ $name ?? '默认值' }}  {{-- 默认值 --}}
```

### **2. 条件判断**
```php
@if($user)
    <p>欢迎，{{ $user->name }}</p>
@else
    <p>请先登录</p>
@endif

@if($score >= 90)
    <span>优秀</span>
@elseif($score >= 60)
    <span>及格</span>
@else
    <span>不及格</span>
@endif
```

### **3. 循环**
```php
@foreach($courses as $course)
    <div class="course">
        <h3>{{ $course->title }}</h3>
        <p>{{ $course->description }}</p>
    </div>
@endforeach

@for($i = 1; $i <= 5; $i++)
    <span>{{ $i }}</span>
@endfor
```

## �� **常用指令**

### **1. 包含文件**
```php
@include('partials.header')  {{-- 包含头部 --}}
@include('partials.footer', ['year' => 2024])  {{-- 传递数据 --}}
```

### **2. 布局模板**
```php
{{-- 主布局：resources/views/layouts/app.blade.php --}}
<!DOCTYPE html>
<html>
<head>
    <title>@yield('title')</title>
</head>
<body>
    @include('partials.header')
    
    <main>
        @yield('content')
    </main>
    
    @include('partials.footer')
</body>
</html>

{{-- 页面：resources/views/courses/index.blade.php --}}
@extends('layouts.app')

@section('title', '课程列表')

@section('content')
    <h1>课程列表</h1>
    @foreach($courses as $course)
        <div>{{ $course->title }}</div>
    @endforeach
@endsection
```

### **3. 组件**
```php
{{-- 创建组件：resources/views/components/course-card.blade.php --}}
<div class="course-card">
    <h3>{{ $title }}</h3>
    <p>{{ $description }}</p>
    <span class="price">¥{{ $price }}</span>
</div>

{{-- 使用组件 --}}
<x-course-card 
    title="Laravel 教程" 
    description="学习 Laravel 框架" 
    price="99" 
/>
```

## �� **实际应用示例**

### **课程列表页面**
```php
{{-- resources/views/courses/index.blade.php --}}
@extends('layouts.app')

@section('title', '课程列表')

@section('content')
<div class="container">
    <h1>课程列表</h1>
    
    @if($courses->count() > 0)
        <div class="course-grid">
            @foreach($courses as $course)
                <div class="course-item">
                    <img src="{{ $course->image }}" alt="{{ $course->title }}">
                    <h3>{{ $course->title }}</h3>
                    <p>{{ $course->description }}</p>
                    
                    @if($course->is_free)
                        <span class="free">免费</span>
                    @else
                        <span class="price">¥{{ $course->price }}</span>
                    @endif
                    
                    <a href="{{ route('courses.show', $course->id) }}" class="btn">
                        查看详情
                    </a>
                </div>
            @endforeach
        </div>
        
        {{-- 分页 --}}
        {{ $courses->links() }}
    @else
        <p>暂无课程</p>
    @endif
</div>
@endsection
```

### **用户资料页面**
```php
{{-- resources/views/user/profile.blade.php --}}
@extends('layouts.app')

@section('title', '个人资料')

@section('content')
<div class="profile">
    <h1>个人资料</h1>
    
    <form method="POST" action="{{ route('user.profile.update') }}">
        @csrf
        
        <div class="form-group">
            <label>用户名</label>
            <input type="text" name="username" value="{{ $user->username }}">
            @error('username')
                <span class="error">{{ $message }}</span>
            @enderror
        </div>
        
        <div class="form-group">
            <label>邮箱</label>
            <input type="email" name="email" value="{{ $user->email }}">
        </div>
        
        <button type="submit">保存</button>
    </form>
    
    {{-- 学习记录 --}}
    <div class="learning-history">
        <h2>学习记录</h2>
        @forelse($user->courses as $course)
            <div class="course-progress">
                <span>{{ $course->title }}</span>
                <span>{{ $course->pivot->progress }}%</span>
            </div>
        @empty
            <p>暂无学习记录</p>
        @endforelse
    </div>
</div>
@endsection
```

## �� **常用技巧**

### **1. 错误处理**
```php
@if($errors->any())
    <div class="alert alert-danger">
        <ul>
            @foreach($errors->all() as $error)
                <li>{{ $error }}</li>
            @endforeach
        </ul>
    </div>
@endif
```

### **2. 旧数据回填**
```php
<input type="text" name="title" value="{{ old('title', $course->title ?? '') }}">
```

### **3. 权限判断**
```php
@can('edit', $course)
    <a href="{{ route('courses.edit', $course->id) }}">编辑</a>
@endcan

@cannot('delete', $course)
    <span>无删除权限</span>
@endcannot
```

## �� **总结**

### **核心语法**
- `{{ }}` - 输出变量
- `{!! !!}` - 输出 HTML
- `@if/@endif` - 条件判断
- `@foreach/@endforeach` - 循环
- `@include` - 包含文件
- `@extends/@section` - 布局模板

### **使用场景**
- 页面渲染
- 数据展示
- 表单处理
- 权限控制

**记住**: Blade = Laravel 的模板引擎，语法简洁，功能强大！