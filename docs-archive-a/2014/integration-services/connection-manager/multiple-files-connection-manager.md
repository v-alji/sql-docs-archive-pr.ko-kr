---
title: 다중 파일 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- Multiple Files connection manager
- connection managers [Integration Services], Multiple Files
- connections [Integration Services], files
- multiple file connections
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9ebd45aa4f0794d98be6a79125bf1874913d491
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659603"
---
# <a name="multiple-files-connection-manager"></a><span data-ttu-id="9d65f-102">다중 파일 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="9d65f-102">Multiple Files Connection Manager</span></span>
  <span data-ttu-id="9d65f-103">다중 파일 연결 관리자를 사용하면 패키지에서 기존 파일 및 폴더를 참조하거나 런타임에 파일 및 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-103">A Multiple Files connection manager enables a package to reference existing files and folders, or to create files and folders at run time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d65f-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 의 기본 제공 태스크 및 데이터 흐름 구성 요소는 다중 파일 연결 관리자를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-104">The built-in tasks and data flow components in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not use the Multiple Files connection manager.</span></span> <span data-ttu-id="9d65f-105">그러나 스크립트 태스크와 스크립트 구성 요소에서 이 연결 관리자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-105">However, you can use this connection manager in the Script task or Script component.</span></span> <span data-ttu-id="9d65f-106">스크립트 태스크에서 연결 관리자를 사용하는 방법은 [스크립트 태스크에서 데이터 원본에 연결](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9d65f-106">For information about how to use connection managers in the Script task, see [Connecting to Data Sources in the Script Task](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md).</span></span> <span data-ttu-id="9d65f-107">스크립트 구성 요소에서 연결 관리자를 사용 하는 방법에 대 한 자세한 내용은 [스크립트 구성 요소에서 데이터 원본에 연결] (. /extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="9d65f-107">For information about how to use connection managers in the Script component, see [Connecting to Data Sources in the Script Component](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md.</span></span>  
  
## <a name="usage-types-of-the-multiple-files-connection-manager"></a><span data-ttu-id="9d65f-108">다중 파일 연결 관리자의 사용 유형</span><span class="sxs-lookup"><span data-stu-id="9d65f-108">Usage Types of the Multiple Files Connection Manager</span></span>  
 <span data-ttu-id="9d65f-109">다중 파일 연결 관리자의 `FileUsageType` 속성은 연결 사용 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-109">The `FileUsageType` property of the Multiple Files connection manager specifies how the connection is used.</span></span> <span data-ttu-id="9d65f-110">다중 파일 연결 관리자에서는 파일이나 폴더를 만들고 기존 파일 또는 기존 폴더를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-110">The Multiple Files connection manager can create files, create folders, use existing files, and use existing folders.</span></span>  
  
 <span data-ttu-id="9d65f-111">다음 표에서는 `FileUsageType` 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-111">The following table lists the values of `FileUsageType`.</span></span>  
  
|<span data-ttu-id="9d65f-112">값</span><span class="sxs-lookup"><span data-stu-id="9d65f-112">Value</span></span>|<span data-ttu-id="9d65f-113">Description</span><span class="sxs-lookup"><span data-stu-id="9d65f-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9d65f-114">**0**</span><span class="sxs-lookup"><span data-stu-id="9d65f-114">**0**</span></span>|<span data-ttu-id="9d65f-115">다중 파일 연결 관리자에서 기존 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-115">Multiple Files connection manager uses an existing file.</span></span>|  
|<span data-ttu-id="9d65f-116">**1**</span><span class="sxs-lookup"><span data-stu-id="9d65f-116">**1**</span></span>|<span data-ttu-id="9d65f-117">다중 파일 연결 관리자에서 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-117">Multiple Files connection manager creates a file.</span></span>|  
|<span data-ttu-id="9d65f-118">**2**</span><span class="sxs-lookup"><span data-stu-id="9d65f-118">**2**</span></span>|<span data-ttu-id="9d65f-119">다중 파일 연결 관리자에서 기존 폴더를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-119">Multiple Files connection manager uses an existing folder.</span></span>|  
|<span data-ttu-id="9d65f-120">**3**</span><span class="sxs-lookup"><span data-stu-id="9d65f-120">**3**</span></span>|<span data-ttu-id="9d65f-121">다중 파일 연결 관리자에서 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-121">Multiple Files connection manager creates a folder.</span></span>|  
  
## <a name="configuration-of-the-multiple-files-connection-manager"></a><span data-ttu-id="9d65f-122">다중 파일 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="9d65f-122">Configuration of the Multiple Files Connection Manager</span></span>  
 <span data-ttu-id="9d65f-123">패키지에 다중 파일 연결 관리자를 추가하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 런타임에 다중 파일 연결로 확인되는 연결 관리자를 만들고, 다중 파일 연결 속성을 설정하고, 다중 파일 연결을 패키지의 `Connections` 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-123">When you add a Multiple Files connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a Multiple Files connection at run time, sets the Multiple Files connection properties, and adds the Multiple Files connection to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="9d65f-124">연결 관리자의 `ConnectionManagerType` 속성이 `MULTIFILE`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-124">The `ConnectionManagerType` property of the connection manager is set to `MULTIFILE`.</span></span>  
  
 <span data-ttu-id="9d65f-125">다음과 같은 방법으로 다중 파일 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-125">You can configure a Multiple Files connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="9d65f-126">파일 및 폴더의 사용 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-126">Specify the usage type of files and folders.</span></span>  
  
-   <span data-ttu-id="9d65f-127">파일 및 폴더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-127">Specify files and folders.</span></span>  
  
-   <span data-ttu-id="9d65f-128">다중 파일 또는 폴더를 사용하는 경우 파일 및 폴더가 액세스되는 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-128">If using multiple files or folders, specify the order in which the files and folders are accessed.</span></span>  
  
 <span data-ttu-id="9d65f-129">다중 파일 연결 관리자에서 다중 파일 및 폴더를 참조하는 경우 파일 및 폴더의 경로는 세로줄 문자(|)로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-129">If the Multiple Files connection manager references multiple files and folders, the paths of the files and folders are separated by the pipe (|) character.</span></span> <span data-ttu-id="9d65f-130">연결 관리자의 `ConnectionString` 속성은 다음 형식을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-130">The `ConnectionString` property of the connection manager has the following format:</span></span>  
  
 \<*path*>|\<*path*>  
  
 <span data-ttu-id="9d65f-131">또한 와일드카드 문자를 사용하여 다중 파일이나 폴더를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-131">You can also specify multiple files or folders using wildcard characters.</span></span> <span data-ttu-id="9d65f-132">예를 들어 C 드라이브의 모든 텍스트 파일을 참조 하려면 속성의 값을 `ConnectionString` c: \* .txt로 설정할 수 있습니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="9d65f-132">For example, to reference all the text files on the C drive, the value of the `ConnectionString` property can be set to C:\\*.txt.</span></span>  
  
 <span data-ttu-id="9d65f-133">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-133">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="9d65f-134">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [파일 연결 관리자 추가 대화 상자 UI 참조](add-file-connection-manager-dialog-box-ui-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d65f-134">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Add File Connection Manager Dialog Box UI Reference](add-file-connection-manager-dialog-box-ui-reference.md).</span></span>  
  
 <span data-ttu-id="9d65f-135">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d65f-135">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
