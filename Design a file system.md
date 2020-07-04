```C#
using System;
using System.Collections.Generic;

// Component interface
public interface IFileComponent
{
    string GetDetailInfo();
    string GetName();
    string GetContent();
    string GetType();
    int GetSize();
    void Delete();
}

// Leaf class
public class File : IFileComponent
{
    private string name;
    private string content;
    private int size;
    public string type;

    public File(string name, string content, int size, string type)
    {
        this.name = name;
        this.content = content;
        this.size = size;
        this.type = type;
    }

    public string GetContent()
    {
        return content;
    }

    public string GetDetailInfo()
    {
        return name + "," + type + "," + content + "," + size;
    }

    public string GetName()
    {
        return name;
    }

    public int GetSize()
    {
        return size;
    }

    string IFileComponent.GetType()
    {
        return type;
    }

    public void Delete()
    {
        Console.WriteLine("Delete " + name);
    }
}

// Composite class
public class Directory : IFileComponent
{
    public List<IFileComponent> FileOrDirCollection;
    private string name;
    public string type;
    private int size;

    public Directory(string name)
    {
        this.name = name;
        FileOrDirCollection = new List<IFileComponent>();
        this.type = "Directory";
        this.size = 0;
    }

    public void AddComponent(IFileComponent fc)
    {
        if (!FileOrDirCollection.Contains(fc))
        {
            FileOrDirCollection.Add(fc);
            size += fc.GetSize();
        }
    }

    public string GetContent()
    {
        return "";
    }

    public string GetDetailInfo()
    {
        return name + "," + type + "," + size;
    }

    public string GetName()
    {
        return name;
    }

    public int GetSize()
    {
        return size;
    }

    string IFileComponent.GetType()
    {
        return type;
    }

    public void Delete()
    {
        Console.WriteLine("Delete " + name);
    }
}

public class FileSystem
{

    private static FileSystem fileSystem;
    private FileSystem()
    { }

    public static FileSystem GetFileSystemInstance()
    {
        if (fileSystem == null)
            fileSystem = new FileSystem();
        return fileSystem;
    }
    public List<IFileComponent> FindAllHtmlFiles(Directory dir, List<IFileComponent> list, string type)
    {
        List<IFileComponent> temp = new List<IFileComponent>();

        foreach(IFileComponent comp in dir.FileOrDirCollection)
        {
            if(comp.GetType() == "Directory")
            {
                FindAllHtmlFiles(comp as Directory, temp, type);
            }

            if (comp.GetType() == type)
                temp.Add(comp);      
        }
        list.AddRange(temp);

        return list;
    }

    static void Main(string[] args)
    {
        File file1 = new File("file1", "content1", 1, "txt");
        File file2 = new File("file2", "content2", 2, "xml");
        File file3 = new File("file3", "content3", 3, "html");
        File file4 = new File("file4", "content4", 4, "html");
        File file5 = new File("file5", "content5", 5, "html");

        /*
            dir1
              --file5
              --dir2
                --file1.txt
                --file2.xml
                --file3.html
                --dir3
                   --file4.html         
         */
 
        Directory dir1 = new Directory("dir1");
        dir1.AddComponent(file5);

        Directory dir2 = new Directory("dir2");
        dir2.AddComponent(file1);
        dir2.AddComponent(file2);
        dir2.AddComponent(file3);
        dir1.AddComponent(dir2);

        Directory dir3 = new Directory("dir3");
        dir3.AddComponent(file4);
        dir2.AddComponent(dir3);

        // Singleton pattern 
        FileSystem system = FileSystem.GetFileSystemInstance();
        List<IFileComponent> htmlFiles = system.FindAllHtmlFiles(dir1, new List<IFileComponent>(), "html");
    }
}
```
