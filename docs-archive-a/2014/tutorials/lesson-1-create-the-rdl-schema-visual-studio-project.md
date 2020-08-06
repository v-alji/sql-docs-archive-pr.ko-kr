---
title: '1 단원: RDL 스키마 Visual Studio 프로젝트 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f420509c-51aa-4170-8c25-64c2954f4bb9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a8411e3f0458ccda8c291d5c86a4467bb051a263
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727527"
---
# <a name="lesson-1-create-the-rdl-schema-visual-studio-project"></a><span data-ttu-id="907f9-102">1단원: RDL Schema Visual Studio 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="907f9-102">Lesson 1: Create the RDL Schema Visual Studio Project</span></span>
  <span data-ttu-id="907f9-103">이 자습서에서는 간단한 콘솔 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-103">For this tutorial, you will create a simple console application.</span></span> <span data-ttu-id="907f9-104">이 자습서에서는에서 개발 하는 것으로 가정 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-104">This tutorial assumes you are developing in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="907f9-105">[!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services에서 실행되는 보고서 서버 웹 서비스에 액세스하는 경우 "ReportServer" 경로에 "_SQLExpress"를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-105">When accessing the Report Server Web service running on [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services, you must append "_SQLExpress" to the "ReportServer" path.</span></span> <span data-ttu-id="907f9-106">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-106">For example:</span></span>  
>   
>  `http://myserver/reportserver_sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-create-the-web-service-proxy"></a><span data-ttu-id="907f9-107">웹 서비스 프록시를 만들려면</span><span class="sxs-lookup"><span data-stu-id="907f9-107">To create the web service proxy</span></span>  
  
1.  <span data-ttu-id="907f9-108">**시작** 메뉴에서 **모든 프로그램**, Microsoft Visual Studio, **Visual Studio 도구**, **Visual Studio 2010 명령 프롬프트**를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-108">From the **Start** menu, select **All Programs**, then Microsoft Visual Studio, then **Visual Studio Tools**, and then **Visual Studio 2010 Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="907f9-109">명령 프롬프트 창에서 C#을 사용 중인 경우 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-109">In the command prompt window, run the following command if you are using C#:</span></span>  
  
    ```  
    wsdl /language:CS /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     <span data-ttu-id="907f9-110">Visual Basic을 사용 중인 경우 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-110">If you are using Visual Basic, then run the following command:</span></span>  
  
    ```  
    wsdl /language:VB /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     <span data-ttu-id="907f9-111">.cs 또는 .vb 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-111">This command generates a .cs or .vb file.</span></span> <span data-ttu-id="907f9-112">이 파일을 애플리케이션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-112">You will add this file to your application.</span></span>  
  
### <a name="to-create-a-console-application"></a><span data-ttu-id="907f9-113">콘솔 애플리케이션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="907f9-113">To create a console application</span></span>  
  
1.  <span data-ttu-id="907f9-114">**파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트** 를 클릭하여 **새 프로젝트** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-114">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="907f9-115">왼쪽 창의 **설치된 템플릿**아래에서 **Visual Basic** 또는 **Visual C#** 노드를 클릭한 다음 확장된 목록에서 프로젝트 형식의 범주를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-115">In the left pane, under **Installed Templates**, click either **Visual Basic** or the **Visual C#** node, and select a category of project types from the expanded list.</span></span>  
  
3.  <span data-ttu-id="907f9-116">**콘솔 애플리케이션** 프로젝트 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-116">Choose the **Console Application** project type.</span></span>  
  
4.  <span data-ttu-id="907f9-117">**이름** 입력란에 프로젝트 이름을</span><span class="sxs-lookup"><span data-stu-id="907f9-117">In the **Name** box, enter a name for your project.</span></span> <span data-ttu-id="907f9-118">이름을 입력 `SampleRDLSchema` 합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-118">Type the name `SampleRDLSchema`.</span></span>  
  
5.  <span data-ttu-id="907f9-119">**위치** 상자에 프로젝트를 저장할 경로를 입력하거나 **찾아보기** 를 클릭하여 원하는 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-119">In the **Location** box, type the path where you want to save your project, or click **Browse** to navigate to the folder.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]<span data-ttu-id="907f9-120">프로젝트의 축소 된 보기가 솔루션 탐색기 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-120">A collapsed view of your project appears in Solution Explorer.</span></span>  
  
7.  <span data-ttu-id="907f9-121">**프로젝트** 메뉴에서 **기존 항목 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-121">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
8.  <span data-ttu-id="907f9-122">생성된 .cs 또는 .vb 파일의 위치로 이동한 다음 파일을 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-122">Navigate to the location for the .cs or .vb file you generated, then select the file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="907f9-123">웹 참조가 작동할 수 있도록 <xref:System.Web.Services> 네임스페이스에 대한 참조도 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-123">You will also need to add a reference to the <xref:System.Web.Services> namespace for your Web reference to work.</span></span>  
  
9. <span data-ttu-id="907f9-124">프로젝트 메뉴에서 **참조 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-124">On the Project menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="907f9-125">**참조 추가** 대화 상자의 **.NET** 탭에서 **System.Web.Services**를 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-125">In the **Add Reference** dialog box, in the **.NET** tab, select **System.Web.Services**, then click **OK**.</span></span>  
  
     <span data-ttu-id="907f9-126">보고서 서버 웹 서비스에 연결 하는 방법에 대 한 자세한 내용은 [웹 서비스 및 .NET Framework를 사용 하 여 응용 프로그램 빌드](../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="907f9-126">For more information about how to connect to the Report Server Web service, see [Building Applications Using the Web Service and the .NET Framework](../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).</span></span>  
  
10. <span data-ttu-id="907f9-127">솔루션 탐색기에서 프로젝트 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-127">In Solution Explorer, expand the project node.</span></span> <span data-ttu-id="907f9-128">Program.cs( [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]의 경우 Module1.vb)라는 기본 이름을 가진 코드 파일이 프로젝트에 추가되었음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-128">You will see a code file with the default name of Program.cs (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) has been added to your project.</span></span>  
  
11. <span data-ttu-id="907f9-129">Program.cs( [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]의 경우 Module1.vb) 파일을 열고 이 코드를 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-129">Open the Program.cs (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) file and replace the code with the following:</span></span>  
  
     <span data-ttu-id="907f9-130">다음 코드는 로드, 업데이트 및 저장 기능을 구현하는 데 사용할 메서드 스텁을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-130">The following code provides the method stubs we will use to implement the Load, Update and Save functionality.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using ReportService2010;  
  
    namespace SampleRDLSchema  
    {  
        class ReportUpdater  
        {  
            ReportingService2010 _reportService;  
  
            static void Main(string[] args)  
            {  
                ReportUpdater reportUpdater = new ReportUpdater();  
                reportUpdater.UpdateReport();  
            }  
  
            private void UpdateReport()  
            {  
                try  
                {  
                    // Set up the Report Service connection  
                    _reportService = new ReportingService2010();  
                    _reportService.Credentials =  
                        System.Net.CredentialCache.DefaultCredentials;  
                    _reportService.Url =  
                       "http://<Server Name>/reportserver/" +  
                                       "reportservice2010.asmx";  
  
                    // Call the methods to update a report definition  
                    LoadReportDefinition();  
                    UpdateReportDefinition();  
                    PublishReportDefinition();  
                }  
                catch (Exception ex)  
                {  
                    System.Console.WriteLine(ex.Message);  
                }  
            }  
  
            private void LoadReportDefinition()  
            {  
                //Lesson 3: Load a report definition from the report   
                //          catalog  
            }  
  
            private void UpdateReportDefinition()  
            {  
                //Lesson 4: Update the report definition using the    
                //          classes generated from the RDL Schema  
            }  
  
            private void PublishReportDefinition()  
            {  
                //Lesson 5: Publish the updated report definition back   
                //          to the report catalog  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.IO  
    Imports System.Text  
    Imports System.Xml  
    Imports System.Xml.Serialization  
    Imports ReportService2010  
  
    Namespace SampleRDLSchema  
  
        Module ReportUpdater  
  
            Private m_reportService As ReportingService2010  
  
            Public Sub Main(ByVal args As String())  
  
                Try  
                    'Set up the Report Service connection  
                    m_reportService = New ReportingService2010  
                    m_reportService.Credentials = _  
                        System.Net.CredentialCache.DefaultCredentials  
                    m_reportService.Url = _  
                        "http:// <Server Name>/reportserver/" & _  
                               "reportservice2010.asmx"  
  
                    'Call the methods to update a report definition  
                    LoadReportDefinition()  
                    UpdateReportDefinition()  
                    PublishReportDefinition()  
                Catch ex As Exception  
                    System.Console.WriteLine(ex.Message)  
                End Try  
  
            End Sub  
  
            Private Sub LoadReportDefinition()  
                'Lesson 3: Load a report definition from the report   
                '          catalog  
            End Sub  
  
            Private Sub UpdateReportDefinition()  
                'Lesson 4: Update the report definition using the   
                '          classes generated from the RDL Schema  
            End Sub  
  
            Private Sub PublishReportDefinition()  
                'Lesson 5: Publish the updated report definition back   
                '          to the report catalog  
            End Sub  
  
        End Module  
  
    End Namespace   
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="907f9-131">다음 단원</span><span class="sxs-lookup"><span data-stu-id="907f9-131">Next Lesson</span></span>  
 <span data-ttu-id="907f9-132">다음 단원에서는 XML 스키마 정의 도구(Xsd.exe)를 사용하여 RDL 스키마의 클래스를 생성하고 이를 프로젝트에 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="907f9-132">In the next lesson, you will use the XML Schema Definition Tool (Xsd.exe) to generate classes from the RDL schema and include them in your project.</span></span> <span data-ttu-id="907f9-133">[Lesson 2: Generate Classes from the RDL Schema using the xsd Tool](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="907f9-133">See [Lesson 2: Generate Classes from the RDL Schema using the xsd Tool](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="907f9-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="907f9-134">See Also</span></span>  
 <span data-ttu-id="907f9-135">[RDL 스키마 &#40;생성 된 클래스를 사용 하 여 보고서 업데이트 (SSRS 자습서&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="907f9-135">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="907f9-136">보고서 정의 언어&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="907f9-136">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
