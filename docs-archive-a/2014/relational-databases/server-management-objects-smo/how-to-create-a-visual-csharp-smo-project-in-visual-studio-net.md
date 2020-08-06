---
title: 'Visual Studio .NET에서 Visual c # SMO 프로젝트 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: stevestein
ms.author: sstein
ms.openlocfilehash: b78820fafd37675332e6703cabbb87e78bde5864
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652761"
---
# <a name="create-a-visual-c-smo-project-in-visual-studio-net"></a><span data-ttu-id="efd9d-102">Visual Studio .NET에서 Visual C# SMO 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="efd9d-102">Create a Visual C# SMO Project in Visual Studio .NET</span></span>
  <span data-ttu-id="efd9d-103">이 섹션에서는 간단한 SMO 콘솔 애플리케이션을 빌드하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-103">This section describes how to build a simple SMO console application.</span></span>  
  
 <span data-ttu-id="efd9d-104">이 예에서는 프로그램이 SMO 형식을 참조할 수 있도록 네임스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-104">This example imports namespaces, which enables the program to reference SMO types.</span></span> <span data-ttu-id="efd9d-105">`Agent` 네임스페이스 가져오기는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-105">The import of the `Agent` namespace is optional.</span></span> <span data-ttu-id="efd9d-106">이 네임스페이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 사용하는 프로그램을 작성하는 경우에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-106">Use it when you are writing a program that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="efd9d-107">`Common` 네임스페이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 보안 연결을 설정하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-107">The `Common` namespace is required to establish a secure connection to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="efd9d-108">`SqlClient` 네임스페이스는 SQL 예외 오류를 처리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-108">The `SqlClient` namespace is used to process SQL exception errors.</span></span>  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a><span data-ttu-id="efd9d-109">Visual Studio .NET에서 Visual C# SMO 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="efd9d-109">Creating a Visual C# SMO project in Visual Studio.NET</span></span>  
  
1.  <span data-ttu-id="efd9d-110">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)](또는 [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)])을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-110">Start [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (or [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).</span></span>  
  
2.  <span data-ttu-id="efd9d-111">**파일** 메뉴에서 **새 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-111">On the **File** menu, click **NewProject.**</span></span> <span data-ttu-id="efd9d-112">**새 프로젝트** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-112">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="efd9d-113">**프로젝트 형식** 대화 상자에서 **Visual c #** 을 선택한 다음 **Windows**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-113">In **Project Types** dialog box, select **Visual C#**, and then select **Windows**.</span></span> <span data-ttu-id="efd9d-114">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]설치 된 템플릿 창에서 **Windows 응용 프로그램**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-114">In the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Installed Templates pane, select **Windows Application**.</span></span>  
  
4.  <span data-ttu-id="efd9d-115">필드 **이름** 필드에 새 응용 프로그램의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-115">(Optional) In the **Name** field, type the name of the new application</span></span>  
  
5.  <span data-ttu-id="efd9d-116">Visual C# 애플리케이션 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-116">Select the Visual C# application type.</span></span> <span data-ttu-id="efd9d-117">다음 예제에서는 **콘솔 응용 프로그램**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-117">For the examples that follow, select **Console Application**.</span></span>  
  
6.  <span data-ttu-id="efd9d-118">**프로젝트** 메뉴에서 **참조 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-118">On the **Project** menu, select **Add Reference**.</span></span> <span data-ttu-id="efd9d-119">**참조 추가** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-119">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="efd9d-120">**찾아보기**를 클릭 하 고 폴더에서 SMO 어셈블리를 찾은 [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] 후 다음 파일을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-120">Click **Browse**, locate the SMO assemblies in the [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] folder, and then select the following files.</span></span> <span data-ttu-id="efd9d-121">SMO 애플리케이션을 빌드하려면 최소한 다음 파일이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-121">These are the minimum files that are required to build an SMO application:</span></span>  
  
     <span data-ttu-id="efd9d-122">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="efd9d-122">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
     <span data-ttu-id="efd9d-123">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="efd9d-123">Microsoft.SqlServer.Smo.dll</span></span>  
  
     <span data-ttu-id="efd9d-124">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="efd9d-124">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span>  
  
     <span data-ttu-id="efd9d-125">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="efd9d-125">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="efd9d-126">두 개 이상의 파일을 선택하려면 `Ctrl` 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-126">Use the `Ctrl` key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="efd9d-127">그 밖에 필요한 SMO 어셈블리를 모두 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-127">Add any additional SMO assemblies that are required.</span></span> <span data-ttu-id="efd9d-128">예를 들어 [!INCLUDE[ssSB](../../includes/sssb-md.md)]를 대상으로 프로그래밍하는 경우 다음 어셈블리를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-128">For example, if you are specifically programming [!INCLUDE[ssSB](../../includes/sssb-md.md)], add the following assemblies:</span></span>  
  
     <span data-ttu-id="efd9d-129">Microsoft.SqlServer.ServiceBrokerEmum.dll</span><span class="sxs-lookup"><span data-stu-id="efd9d-129">Microsoft.SqlServer.ServiceBrokerEmum.dll</span></span>  
  
9. <span data-ttu-id="efd9d-130">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-130">Click **Open**.</span></span>  
  
10. <span data-ttu-id="efd9d-131">**보기** 메뉴에서 **코드**를 클릭 합니다. 또는 Program1.cs [Design] windows를 선택 하 고 windows form을 두 번 클릭 하 여 코드 창을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-131">On the **View** menu, click **Code**.-Or-Select the Program1.cs [Design] Windows and double-click the windows form to show the code window.</span></span>  
  
11. <span data-ttu-id="efd9d-132">이 코드에서 네임스페이스 문 앞에 다음 `using` 문을 입력하여 SMO 네임스페이스의 형식을 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-132">In the code, before the namespace statement, type the following `using` statements to qualify the types in the SMO namespace:</span></span>  
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
12. <span data-ttu-id="efd9d-133">SMO의 Microsoft.SqlServer.Management.Smo 아래에는 Microsoft.SqlServer.Management.Smo.Agent와 같은 다양한 네임스페이스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-133">SMO has various namespaces under Microsoft.SqlServer.Management.Smo, such as Microsoft.SqlServer.Management.Smo.Agent.</span></span> <span data-ttu-id="efd9d-134">이러한 네임스페이스를 필요에 따라 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-134">Add these namespaces as they are required.</span></span>  
  
13. <span data-ttu-id="efd9d-135">이제 SMO 코드를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efd9d-135">You can now add your SMO code.</span></span>  
  
  
