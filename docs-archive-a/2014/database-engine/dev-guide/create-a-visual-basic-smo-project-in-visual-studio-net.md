---
title: Visual Studio .NET에서 Visual Basic SMO 프로젝트 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic [SMO]
ms.assetid: d7a3892c-0f1c-4c4d-8480-b58dce3720bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 844d27ab6aadbc972c6282c79adb13e15d55c322
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742547"
---
# <a name="create-a-visual-basic-smo-project-in-visual-studio-net"></a><span data-ttu-id="93209-102">Visual Studio .NET에서 Visual Basic SMO 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="93209-102">Create a Visual Basic SMO Project in Visual Studio .NET</span></span>
  <span data-ttu-id="93209-103">이 섹션에서는 간단한 SMO 콘솔 애플리케이션을 빌드하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-103">This section describes how to build a simple SMO console application.</span></span>  
  
 <span data-ttu-id="93209-104">이 예에서는 프로그램이 SMO 형식을 참조할 수 있도록 네임스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="93209-104">This example imports namespaces, which enables the program to reference SMO types.</span></span> <span data-ttu-id="93209-105">`Agent` 네임스페이스 가져오기는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="93209-105">The import of the `Agent` namespace is optional.</span></span> <span data-ttu-id="93209-106">이 네임스페이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하는 프로그램을 작성하는 경우에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-106">Use it when you are writing a program that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="93209-107">`Common` 네임스페이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 보안 연결을 설정하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-107">The `Common` namespace is required to establish a secure connection to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="93209-108">`SqlClient` 네임스페이스는 SQL 예외 오류를 처리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="93209-108">The `SqlClient` namespace is used to process SQL exception errors.</span></span>  
  
### <a name="creating-a-visual-basic-smo-project-in-visual-studionet"></a><span data-ttu-id="93209-109">Visual Studio.NET에서 Visual Basic SMO 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="93209-109">Creating a Visual Basic SMO project in Visual Studio.NET</span></span>  
  
1.  <span data-ttu-id="93209-110">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)](또는 [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)])을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-110">Start [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (or [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).</span></span>  
  
2.  <span data-ttu-id="93209-111">**파일** 메뉴에서 **새 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-111">On the **File** menu, click **NewProject.**</span></span> <span data-ttu-id="93209-112">**새 프로젝트** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="93209-112">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="93209-113">**프로젝트 형식** 대화 상자에서 **Visual Basic**를 선택한 다음 **Windows**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-113">In **Project Types** dialog box, select **Visual Basic**, and then select **Windows**.</span></span> <span data-ttu-id="93209-114">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]설치 된 템플릿 창에서 **콘솔 응용 프로그램을 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="93209-114">In the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Installed Templates pane, select **Console Application.**</span></span>  
  
4.  <span data-ttu-id="93209-115">필드 **이름** 필드에 새 응용 프로그램의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-115">(Optional) In the **Name** field, type the name of the new application.</span></span>  
  
5.  <span data-ttu-id="93209-116">**확인** 을 클릭 하 여 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 콘솔 응용 프로그램 템플릿을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-116">Click **OK** to load the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] console application template.</span></span>  
  
6.  <span data-ttu-id="93209-117">**프로젝트** 메뉴에서 **참조 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-117">On the **Project** menu, select **Add Reference**.</span></span> <span data-ttu-id="93209-118">**참조 추가** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="93209-118">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="93209-119">**찾아보기**를 클릭 하 고 C:\PROGRAM Files\Microsoft SQL Server\120\SDK\Assemblies 폴더에서 SMO 어셈블리를 찾은 후 다음 파일을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-119">Click **Browse**, locate the SMO assemblies in the C:\Program Files\Microsoft SQL Server\120\SDK\Assemblies folder, and then select the following files.</span></span> <span data-ttu-id="93209-120">SMO 애플리케이션을 빌드하려면 최소한 다음 파일이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-120">These are the minimum files that are required to build an SMO application:</span></span>  
  
     <span data-ttu-id="93209-121">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="93209-121">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
     <span data-ttu-id="93209-122">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="93209-122">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
     <span data-ttu-id="93209-123">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="93209-123">Microsoft.SqlServer.Smo.dll</span></span>  
  
     <span data-ttu-id="93209-124">Microsoft.SqlServer.Management.Sdk.Sfc</span><span class="sxs-lookup"><span data-stu-id="93209-124">Microsoft.SqlServer.Management.Sdk.Sfc</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="93209-125">두 개 이상의 파일을 선택하려면 `Ctrl` 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-125">Use the `Ctrl` key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="93209-126">그 밖에 필요한 SMO 어셈블리를 모두 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-126">Add any additional SMO assemblies that are required.</span></span> <span data-ttu-id="93209-127">예를 들어 [!INCLUDE[ssSB](../../includes/sssb-md.md)]를 대상으로 프로그래밍하는 경우 다음 어셈블리를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-127">For example, if you are specifically programming [!INCLUDE[ssSB](../../includes/sssb-md.md)], add the following assemblies:</span></span>  
  
     <span data-ttu-id="93209-128">Microsoft.SqlServer.ServiceBrokerEmum.dll</span><span class="sxs-lookup"><span data-stu-id="93209-128">Microsoft.SqlServer.ServiceBrokerEmum.dll</span></span>  
  
9. <span data-ttu-id="93209-129">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-129">Click **Open**.</span></span>  
  
10. <span data-ttu-id="93209-130">**보기** 메뉴에서 **코드**를 클릭 합니다. 또는 module1.vb 창을 선택 하 여 코드 창을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-130">On the **View** menu, click **Code**.-Or-Select the Module1.vb window to show the code window.</span></span>  
  
11. <span data-ttu-id="93209-131">코드에서 모든 선언 앞에 다음 **Imports** 문을 입력 하 여 SMO 네임 스페이스의 형식을 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-131">In the code, before any declarations, type the following **Imports** statements to qualify the types in the SMO namespace.</span></span>  
  
    ```  
    Imports Microsoft.SqlServer.Management.Smo  
    Imports Microsoft.SqlServer.Management.Common  
    ```  
  
12. <span data-ttu-id="93209-132">SMO의 Microsoft.SqlServer.Management.Smo 아래에는 Microsoft.SqlServer.Management.Smo.Agent와 같은 다양한 네임스페이스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93209-132">SMO has various namespaces under Microsoft.SqlServer.Management.Smo, such as Microsoft.SqlServer.Management.Smo.Agent.</span></span> <span data-ttu-id="93209-133">이러한 네임스페이스를 필요에 따라 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="93209-133">Add these namespaces as they are required.</span></span>  
  
13. <span data-ttu-id="93209-134">이제 SMO 코드를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93209-134">You can now add your SMO code.</span></span>  
  
  
