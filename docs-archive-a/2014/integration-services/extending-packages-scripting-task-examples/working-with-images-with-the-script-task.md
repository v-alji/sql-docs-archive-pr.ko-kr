---
title: 스크립트 태스크를 사용한 이미지 작업 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- graphics [Integration Services]
- Script task [Integration Services], images
- Drawing namespace
- images [Integration Services]
- SSIS Script task, images
- Script task [Integration Services], examples
- thumbnails [Integration Services]
- System.Drawing namespace
- JPEG format [Integration Services]
- .jpeg files
ms.assetid: 74aeb7ab-51b2-4b9f-84ee-0b46a7908ab9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 75a5b72f87a4463d7270dc9f28529a81525860cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651202"
---
# <a name="working-with-images-with-the-script-task"></a><span data-ttu-id="ad1b8-102">스크립트 태스크를 사용한 이미지 작업</span><span class="sxs-lookup"><span data-stu-id="ad1b8-102">Working with Images with the Script Task</span></span>
  <span data-ttu-id="ad1b8-103">제품 또는 사용자 데이터베이스에는 텍스트 및 숫자 데이터 외에 이미지도 포함되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-103">A database of products or users frequently includes images in addition to text and numeric data.</span></span> <span data-ttu-id="ad1b8-104">Microsoft .NET Framework의 `System.Drawing` 네임스페이스에서는 이미지 조작을 위한 클래스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-104">The `System.Drawing` namespace in the Microsoft .NET Framework provides classes for manipulating images.</span></span>  
  
 [<span data-ttu-id="ad1b8-105">예 1: JPEG 형식으로 이미지 변환</span><span class="sxs-lookup"><span data-stu-id="ad1b8-105">Example 1: Convert Images to JPEG Format</span></span>](#example1)  
  
 [<span data-ttu-id="ad1b8-106">예 2: 썸네일 이미지 만들기 및 저장</span><span class="sxs-lookup"><span data-stu-id="ad1b8-106">Example 2: Create and Save Thumbnail Images</span></span>](#example2)  
  
> [!NOTE]  
>  <span data-ttu-id="ad1b8-107">여러 패키지에서 쉽게 다시 사용할 수 있는 태스크를 만들려면 이 스크립트 태스크 예제에 있는 코드를 바탕으로 사용자 지정 태스크를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-107">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="ad1b8-108">자세한 내용은 [사용자 지정 태스크 개발](../extending-packages-custom-objects/task/developing-a-custom-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-108">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
##  <a name="example-1-description-convert-images-to-jpeg-format"></a><a name="example1"></a><span data-ttu-id="ad1b8-109">예 1 설명: JPEG 형식으로 이미지 변환</span><span class="sxs-lookup"><span data-stu-id="ad1b8-109">Example 1 Description: Convert Images to JPEG Format</span></span>  
 <span data-ttu-id="ad1b8-110">다음 예에서는 변수로 지정된 이미지 파일을 열고 인코더를 사용하여 이 파일을 압축된 JPEG 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-110">The following example opens an image file specified by a variable and saves it as a compressed JPEG file by using an encoder.</span></span> <span data-ttu-id="ad1b8-111">인코더 정보를 검색하는 코드는 프라이빗 함수에 캡슐화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-111">The code to retrieve encoder information is encapsulated in a private function.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-a-single-image-file"></a><span data-ttu-id="ad1b8-112">이 스크립트 태스크 예를 단일 이미지 파일에 사용할 수 있도록 구성하려면</span><span class="sxs-lookup"><span data-stu-id="ad1b8-112">To configure this Script Task example for use with a single image file</span></span>  
  
1.  <span data-ttu-id="ad1b8-113">`CurrentImageFile`이라는 문자열 변수를 만들고 해당 값을 기존 이미지 파일의 경로 및 파일 이름으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-113">Create a string variable named `CurrentImageFile` and set its value to the path and file name of an existing image file.</span></span>  
  
2.  <span data-ttu-id="ad1b8-114">**스크립트 태스크 편집기**의 **스크립트** 페이지에서 `CurrentImageFile` 속성에 변수를 추가 `ReadOnlyVariables` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-114">On the **Script** page of the **Script Task Editor**, add the `CurrentImageFile` variable to the `ReadOnlyVariables` property.</span></span>  
  
3.  <span data-ttu-id="ad1b8-115">스크립트 프로젝트에서 `System.Drawing` 네임스페이스에 대한 참조를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-115">In the script project, set a reference to the `System.Drawing` namespace.</span></span>  
  
4.  <span data-ttu-id="ad1b8-116">코드에서 `Imports` 문을 사용하여 `System.Drawing` 및 `System.IO` 네임스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-116">In your code, use `Imports` statements to import the `System.Drawing` and `System.IO` namespaces.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-multiple-image-files"></a><span data-ttu-id="ad1b8-117">이 스크립트 태스크 예를 여러 이미지 파일에 사용할 수 있도록 구성하려면</span><span class="sxs-lookup"><span data-stu-id="ad1b8-117">To configure this Script Task example for use with multiple image files</span></span>  
  
1.  <span data-ttu-id="ad1b8-118">Foreach 루프 컨테이너 내에 스크립트 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-118">Place the Script task within a Foreach Loop container.</span></span>  
  
2.  <span data-ttu-id="ad1b8-119">**Foreach 루프 편집기**의 **컬렉션** 페이지에서 열거자로 **Foreach File 열거자**를 선택하고 원본 파일의 경로 및 파일 마스크(예: "\*.bmp")를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-119">On the **Collection** page of the **Foreach Loop Editor**, select the **Foreach File Enumerator** as the enumerator, and specify the path and file mask of the source files, such as "\*.bmp."</span></span>  
  
3.  <span data-ttu-id="ad1b8-120">**변수 매핑** 페이지에서 `CurrentImageFile` 변수를 인덱스 0으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-120">On the **Variable Mappings** page, map the `CurrentImageFile` variable to Index 0.</span></span> <span data-ttu-id="ad1b8-121">이 변수는 현재 파일 이름을 열거자의 각 반복에 있는 스크립트 태스크에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-121">This variable passes the current file name to the Script task on each iteration of the enumerator.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ad1b8-122">이러한 단계는 단일 이미지 파일에 사용하기 위한 절차에 나열된 단계에 추가적으로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-122">These steps are in addition to the steps listed in the procedure for use with a single image file.</span></span>  
  
### <a name="example-1-code"></a><span data-ttu-id="ad1b8-123">예 1 코드</span><span class="sxs-lookup"><span data-stu-id="ad1b8-123">Example 1 Code</span></span>  
  
```vb  
Public Sub Main()  
  
    'Create and initialize variables.  
    Dim currentFile As String  
    Dim newFile As String  
    Dim bmp As Bitmap  
    Dim eps As New Imaging.EncoderParameters(1)  
    Dim ici As Imaging.ImageCodecInfo  
    Dim supportedExtensions() As String = _  
        {".BMP", ".GIF", ".JPG", ".JPEG", ".EXIF", ".PNG", _  
        ".TIFF", ".TIF", ".ICO", ".ICON"}  
  
    Try  
        'Store the variable in a string for local manipulation.  
        currentFile = Dts.Variables("CurrentImageFile").Value.ToString  
        'Check the extension of the file against a list of  
        'files that the Bitmap class supports.  
        If Array.IndexOf(supportedExtensions, _  
            Path.GetExtension(currentFile).ToUpper) > -1 Then  
  
            'Load the file.  
            bmp = New Bitmap(currentFile)  
  
            'Calculate the new name for the compressed image.  
            'Note: This will overwrite existing JPEGs.  
            newFile = Path.Combine( _  
                Path.GetDirectoryName(currentFile), _  
                String.Concat(Path.GetFileNameWithoutExtension(currentFile), _  
                ".jpg"))  
  
            'Specify the compression ratio (0=worst quality, 100=best quality).  
            eps.Param(0) = New Imaging.EncoderParameter( _  
                Imaging.Encoder.Quality, 75)  
  
            'Retrieve the ImageCodecInfo associated with the jpeg format.  
            ici = GetEncoderInfo("image/jpeg")  
  
            'Save the file, compressing it into the jpeg encoding.  
            bmp.Save(newFile, ici, eps)  
        Else  
            'The file is not supported by the Bitmap class.  
            Dts.Events.FireWarning(0, "Image Resampling Sample", _  
                "File " & currentFile & " is not a supported format.", _  
                "", 0)  
         End If  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Image Resampling Sample", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
  
Private Function GetEncoderInfo(ByVal mimeType As String) As Imaging.ImageCodecInfo  
  
    'The available image codecs are returned as an array,  
    'which requires code to iterate until the specified codec is found.  
  
    Dim count As Integer  
    Dim encoders() As Imaging.ImageCodecInfo  
  
    encoders = Imaging.ImageCodecInfo.GetImageEncoders()  
  
    For count = 0 To encoders.Length  
        If encoders(count).MimeType = mimeType Then  
            Return encoders(count)  
        End If  
    Next  
  
    'This point is only reached if a codec is not found.  
    Err.Raise(513, "Image Resampling Sample", String.Format( _  
        "The {0} codec is not available. Unable to compress file.", _  
            mimeType))  
    Return Nothing  
  
End Function  
  
```  
  
##  <a name="example-2-description-create-and-save-thumbnail-images"></a><a name="example2"></a> <span data-ttu-id="ad1b8-124">예 2 설명: 썸네일 이미지 만들기 및 저장</span><span class="sxs-lookup"><span data-stu-id="ad1b8-124">Example 2 Description: Create and Save Thumbnail Images</span></span>  
 <span data-ttu-id="ad1b8-125">다음 예에서는 변수로 지정된 이미지 파일을 열고, 가로 세로 비율을 일정하게 유지하면서 이미지의 축소판 그림을 만들고, 이 축소판 그림을 수정된 파일 이름으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-125">The following example opens an image file specified by a variable, creates a thumbnail of the image while maintaining a constant aspect ratio, and saves the thumbnail with a modified file name.</span></span> <span data-ttu-id="ad1b8-126">가로 세로 비율을 일정하게 유지하면서 축소판 그림의 높이와 너비를 계산하는 코드는 프라이빗 서브루틴에 캡슐화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-126">The code that calculates the height and width of the thumbnail while maintaining a constant aspect ratio is encapsulated in a private subroutine.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-a-single-image-file"></a><span data-ttu-id="ad1b8-127">이 스크립트 태스크 예를 단일 이미지 파일에 사용할 수 있도록 구성하려면</span><span class="sxs-lookup"><span data-stu-id="ad1b8-127">To configure this Script Task example for use with a single image file</span></span>  
  
1.  <span data-ttu-id="ad1b8-128">`CurrentImageFile`이라는 문자열 변수를 만들고 해당 값을 기존 이미지 파일의 경로 및 파일 이름으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-128">Create a string variable named `CurrentImageFile` and set its value to the path and file name of an existing image file.</span></span>  
  
2.  <span data-ttu-id="ad1b8-129">또한 `MaxThumbSize`라는 정수 변수를 만들고 100과 같이 값을 픽셀 단위로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-129">Also create the `MaxThumbSize` integer variable and assign a value in pixels, such as 100.</span></span>  
  
3.  <span data-ttu-id="ad1b8-130">**스크립트 태스크 편집기**의 **스크립트** 페이지에서 두 변수를 모두 속성에 추가 `ReadOnlyVariables` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-130">On the **Script** page of the **Script Task Editor**, add both variables to the `ReadOnlyVariables` property.</span></span>  
  
4.  <span data-ttu-id="ad1b8-131">스크립트 프로젝트에서 `System.Drawing` 네임스페이스에 대한 참조를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-131">In the script project, set a reference to the `System.Drawing` namespace.</span></span>  
  
5.  <span data-ttu-id="ad1b8-132">코드에서 `Imports` 문을 사용하여 `System.Drawing` 및 `System.IO` 네임스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-132">In your code, use `Imports` statements to import the `System.Drawing` and `System.IO` namespaces.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-multiple-image-files"></a><span data-ttu-id="ad1b8-133">이 스크립트 태스크 예를 여러 이미지 파일에 사용할 수 있도록 구성하려면</span><span class="sxs-lookup"><span data-stu-id="ad1b8-133">To configure this Script Task example for use with multiple image files</span></span>  
  
1.  <span data-ttu-id="ad1b8-134">Foreach 루프 컨테이너 내에 스크립트 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-134">Place the Script task within a Foreach Loop container.</span></span>  
  
2.  <span data-ttu-id="ad1b8-135">**Foreach 루프 편집기**의 **컬렉션** 페이지에서 **열거자**로 **Foreach File 열거자**를 선택하고 원본 파일의 경로 및 파일 마스크(예: "\*.jpg")를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-135">On the **Collection** page of the **Foreach Loop Editor**, select the **Foreach File Enumerator** as the **Enumerator**, and specify the path and file mask of the source files, such as "\*.jpg."</span></span>  
  
3.  <span data-ttu-id="ad1b8-136">**변수 매핑** 페이지에서 `CurrentImageFile` 변수를 인덱스 0으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-136">On the **Variable Mappings** page, map the `CurrentImageFile` variable to Index 0.</span></span> <span data-ttu-id="ad1b8-137">이 변수는 현재 파일 이름을 열거자의 각 반복에 있는 스크립트 태스크에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-137">This variable passes the current file name to the Script task on each iteration of the enumerator.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ad1b8-138">이러한 단계는 단일 이미지 파일에 사용하기 위한 절차에 나열된 단계에 추가적으로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-138">These steps are in addition to the steps listed in the procedure for use with a single image file.</span></span>  
  
### <a name="example-2-code"></a><span data-ttu-id="ad1b8-139">예 2 코드</span><span class="sxs-lookup"><span data-stu-id="ad1b8-139">Example 2 Code</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim currentImageFile As String  
    Dim currentImage As Image  
    Dim maxThumbSize As Integer  
    Dim thumbnailImage As Image  
    Dim thumbnailFile As String  
    Dim thumbnailHeight As Integer  
    Dim thumbnailWidth As Integer  
  
    currentImageFile = Dts.Variables("CurrentImageFile").Value.ToString  
    thumbnailFile = Path.Combine( _  
        Path.GetDirectoryName(currentImageFile), _  
        String.Concat(Path.GetFileNameWithoutExtension(currentImageFile), _  
        "_thumbnail.jpg"))  
  
    Try  
        currentImage = Image.FromFile(currentImageFile)  
  
        maxThumbSize = CType(Dts.Variables("MaxThumbSize").Value, Integer)  
        CalculateThumbnailSize( _  
            maxThumbSize, currentImage, thumbnailWidth, thumbnailHeight)  
  
        thumbnailImage = currentImage.GetThumbnailImage( _  
           thumbnailWidth, thumbnailHeight, Nothing, Nothing)  
        thumbnailImage.Save(thumbnailFile)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, "Script Task Example", _  
        ex.Message & ControlChars.CrLf & ex.StackTrace, _  
        String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
  
Private Sub CalculateThumbnailSize( _  
    ByVal maxSize As Integer, ByVal sourceImage As Image, _  
    ByRef thumbWidth As Integer, ByRef thumbHeight As Integer)  
  
    If sourceImage.Width > sourceImage.Height Then  
        thumbWidth = maxSize  
        thumbHeight = CInt((maxSize / sourceImage.Width) * sourceImage.Height)  
    Else  
        thumbHeight = maxSize  
        thumbWidth = CInt((maxSize / sourceImage.Height) * sourceImage.Width)  
    End If  
  
End Sub  
```  
  
```csharp  
bool ThumbnailCallback()  
        {  
            return false;  
        }  
        public void Main()  
        {  
  
            string currentImageFile;  
            Image currentImage;  
            int maxThumbSize;  
            Image thumbnailImage;  
            string thumbnailFile;  
            int thumbnailHeight = 0;  
            int thumbnailWidth = 0;  
  
            currentImageFile = Dts.Variables["CurrentImageFile"].Value.ToString();  
            thumbnailFile = Path.Combine(Path.GetDirectoryName(currentImageFile), String.Concat(Path.GetFileNameWithoutExtension(currentImageFile), "_thumbnail.jpg"));  
  
            try  
            {  
  
                currentImage = Image.FromFile(currentImageFile);  
  
                maxThumbSize = (int)Dts.Variables["MaxThumbSize"].Value;  
                CalculateThumbnailSize(maxThumbSize, currentImage, ref thumbnailWidth, ref thumbnailHeight);  
  
                Image.GetThumbnailImageAbort myCallback = new Image.GetThumbnailImageAbort(ThumbnailCallback);  
  
                thumbnailImage = currentImage.GetThumbnailImage(thumbnailWidth, thumbnailHeight, ThumbnailCallback, IntPtr.Zero);  
                thumbnailImage.Save(thumbnailFile);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
  
        private void CalculateThumbnailSize(int maxSize, Image sourceImage, ref int thumbWidth, ref int thumbHeight)  
        {  
  
            if (sourceImage.Width > sourceImage.Height)  
            {  
                thumbWidth = maxSize;  
                thumbHeight = (int)(sourceImage.Height * maxSize / sourceImage.Width);  
            }  
            else  
            {  
                thumbHeight = maxSize;  
                thumbWidth = (int)(sourceImage.Width * maxSize / sourceImage.Height);  
  
            }  
  
        }  
  
```  
  
<span data-ttu-id="ad1b8-140">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="ad1b8-140">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ad1b8-141">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-141">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ad1b8-142">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-142">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ad1b8-143">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="ad1b8-143">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
