
Runing
------
1. 源码
::
        @settings:
            language = Python;
            autoimport = True;
            compile_only = False;
        @qcodes:
        // The D_J Algorithm of 2 quantum bits

        D_J(qvec q,cvec c){
            RX(q[1],Pi);
            H(q[0]);
            H(q[1]);
            CNOT(q[0],q[1]);
            H(q[0]);
            Measure(q[0],c[0]);
        }

        @script:
        init(QuantumMachine_type.CPU_SINGLE_THREAD)
        q = qAlloc_many(2)
        c = cAlloc_many(1)
        qprog1 = D_J(q,c)
        result = directly_run(qprog1)
        print(result)

        finalize()

2. 根据标识切割源码
    - Python源码处理
    ::
        def python_data(qrunes_file,sep_path,language_type):
        """generate python file
        - qrunes_file -- The data address to load
        - sep_path -- Built-in code path
        - language_type -- language type
        """
        generate_import_py_file(qrunes_file,sep_path,language_type)
        path=sep_path + "\\qcodes.q"
        with open(path, 'w', encoding = 'utf-8') as f:
            f.write(utils.get_qcodes(qrunes_file))
        generate_package_name = utils.get_filename(qrunes_file)+'_python'
        file_generate_path = utils.makedirs(os.path.dirname(qrunes_file)+"\\"+generate_package_name)
        script_data = utils.get_script(qrunes_file)
        path =  file_generate_path + '\\script.py'
        with open(path, 'w', encoding = 'utf-8') as f:
            f.write(script_data)
        qcodeHandle.main(qrunes_file,file_generate_path,language_type)
    - C++源码处理
    ::
        def cpp_data(qrunes_file,sep_path,language_type):
        """generate c++ file
        - qrunes_file -- The data address to load
        - sep_path -- Built-in code path
        - language_type -- language type
        """
        generate_import_cpp_file(qrunes_file,sep_path,language_type)
        generate_package_name = utils.get_filename(qrunes_file)+'_cpp'
        file_generate_path = utils.makedirs(os.path.dirname(qrunes_file)+"\\"+generate_package_name)
        #generate sh.bat file
        path = sep_path + "\\sh.bat"
        with open(path, 'w', encoding = 'utf-8') as f:
            f.write(utils.get_sh(qrunes_file,file_generate_path))
        #generate qcodes.p file
        path = sep_path + "\\qcodes.p"
        with open(path, 'w') as f:
            f.write(utils.get_qcodes(qrunes_file))# Get qcodes Code
        #generate script.cpp file
        script_data = utils.get_script(qrunes_file)
        path=file_generate_path + "\\script.cpp"
        with open(path, 'w', encoding = 'utf-8') as f:
            f.write(script_data)# Get Script Code
        qcodeHandle.main(qrunes_file,file_generate_path,language_type)

3. 解析qcodes代码
    
    - 源码：
    ::
        D_J(qvec q,cvec c){
            RX(q[1],Pi);
            H(q[0]);
            H(q[1]);
            CNOT(q[0],q[1]);
            H(q[0]);
            Measure(q[0],c[0]);
        }
    - python代码：
    ::
        def D_J(q,c):
        _qprog = QProg()
        _qprog.insert(RX(q[1],3.14159265358979))
        _qprog.insert(H(q[0]))
        _qprog.insert(H(q[1]))
        _qprog.insert(CNOT(q[0],q[1]))
        _qprog.insert(H(q[0]))
        _qprog.insert(Measure(q[0],c[0]))
        return _qprog

4. running过程
    - 使用nodejs运行python代码：
    ::
        CommandExecutor.exec('python', [path.dirname(file_path)+generate_file_path+'\\script.py'])
            .then(stdout => {
                vscode.window.showInformationMessage('👌  Run Successfully');
                return resolve(stdout);
            })
            .catch(err => {
                QLogger.error(err, this);
                vscode.window.showErrorMessage(err);
                return reject(err);
            });
