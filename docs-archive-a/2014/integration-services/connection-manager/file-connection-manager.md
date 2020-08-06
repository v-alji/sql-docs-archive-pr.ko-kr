---
title: 파일 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- files [Integration Services]
- connection managers [Integration Services], File
- connections [Integration Services], files
- File connection manager
ms.assetid: 019078bc-44ee-4975-9169-0f9a89e3f3be
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cebb5438003c6b14c547d14012ff1bc1175a706d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738566"
---
# <a name="file-connection-manager"></a><span data-ttu-id="cecff-102">파일 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="cecff-102">File Connection Manager</span></span>
  <span data-ttu-id="cecff-103">파일 연결 관리자를 사용하면 패키지에서 기존 파일 또는 폴더를 참조하거나 런타임에 파일 또는 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-103">A File connection manager enables a package to reference an existing file or folder, or to create a file or folder at run time.</span></span> <span data-ttu-id="cecff-104">예를 들어 Excel 파일을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-104">For example, you can reference an Excel file.</span></span> <span data-ttu-id="cecff-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]의 특정 구성 요소는 파일에 있는 정보를 사용하여 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-105">Certain components in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] use information in files to perform their work.</span></span> <span data-ttu-id="cecff-106">예를 들어 SQL 실행 태스크에서는 해당 태스크가 실행하는 SQL 문이 포함된 파일을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-106">For example, an Execute SQL task can reference a file that contains the SQL statements that the task executes.</span></span> <span data-ttu-id="cecff-107">다른 구성 요소는 파일에 대한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-107">Other components perform operations on files.</span></span> <span data-ttu-id="cecff-108">예를 들어 파일 시스템 태스크는 파일을 참조하여 새 위치로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-108">For example, the File System task can reference a file to copy it to a new location.</span></span>  
  
## <a name="usage-types-of-the-file-connection-manager"></a><span data-ttu-id="cecff-109">파일 연결 관리자의 사용 유형</span><span class="sxs-lookup"><span data-stu-id="cecff-109">Usage Types of the File Connection Manager</span></span>  
 <span data-ttu-id="cecff-110">파일 연결 관리자의 `FileUsageType` 속성은 파일 연결 사용 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-110">The `FileUsageType` property of the File connection manager specifies how the file connection is used.</span></span> <span data-ttu-id="cecff-111">파일 연결 관리자에서는 파일이나 폴더를 만들고 기존 파일 또는 기존 폴더를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-111">The File connection manager can create a file, create a folder, use an existing file, or use an existing folder.</span></span>  
  
 <span data-ttu-id="cecff-112">다음 표에서는 `FileUsageType` 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-112">The following table lists the values of `FileUsageType`.</span></span>  
  
|<span data-ttu-id="cecff-113">값</span><span class="sxs-lookup"><span data-stu-id="cecff-113">Value</span></span>|<span data-ttu-id="cecff-114">Description</span><span class="sxs-lookup"><span data-stu-id="cecff-114">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="cecff-115">파일 연결 관리자에서 기존 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-115">File connection manager uses an existing file.</span></span>|  
|`1`|<span data-ttu-id="cecff-116">파일 연결 관리자에서 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-116">File connection manager creates a file.</span></span>|  
|`2`|<span data-ttu-id="cecff-117">파일 연결 관리자에서 기존 폴더를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-117">File connection manager uses an existing folder.</span></span>|  
|`3`|<span data-ttu-id="cecff-118">파일 연결 관리자에서 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-118">File connection manager creates a folder.</span></span>|  
  
## <a name="multiple-file-or-folder-connections"></a><span data-ttu-id="cecff-119">다중 파일 또는 폴더 연결</span><span class="sxs-lookup"><span data-stu-id="cecff-119">Multiple File or Folder Connections</span></span>  
 <span data-ttu-id="cecff-120">파일 연결 관리자는 파일 또는 폴더를 하나만 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-120">The File connection manager can reference only one file or folder.</span></span> <span data-ttu-id="cecff-121">파일이나 폴더를 여러 개 참조하려면 파일 연결 관리자 대신 다중 파일 연결 관리자를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="cecff-121">To reference multiple files or folders, use a Multiple Files connection manager instead of a File connection manager.</span></span> <span data-ttu-id="cecff-122">자세한 내용은 [Multiple Files Connection Manager](multiple-files-connection-manager.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cecff-122">For more information, see [Multiple Files Connection Manager](multiple-files-connection-manager.md).</span></span>  
  
## <a name="configuration-of-the-file-connection-manager"></a><span data-ttu-id="cecff-123">파일 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="cecff-123">Configuration of the File Connection Manager</span></span>  
 <span data-ttu-id="cecff-124">패키지에 파일 연결 관리자를 추가하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 런타임에 파일 연결로 확인되는 연결 관리자를 만들고, 파일 연결 속성을 설정하고, 파일 연결을 패키지의 `Connections` 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-124">When you add a File connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a File connection at run time, sets the File connection properties, and adds the File connection to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="cecff-125">연결 관리자의 `ConnectionManagerType` 속성이 `FILE`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-125">The `ConnectionManagerType` property of the connection manager is set to `FILE`.</span></span>  
  
 <span data-ttu-id="cecff-126">다음과 같은 방법으로 파일 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-126">You can configure a File connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="cecff-127">사용 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-127">Specify the usage type.</span></span>  
  
-   <span data-ttu-id="cecff-128">파일 또는 폴더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-128">Specify a file or folder.</span></span>  
  
 <span data-ttu-id="cecff-129">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 속성 창에 식을 지정하여 파일 연결 관리자에 대한 ConnectionString 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-129">You can set the ConnectionString property for the File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="cecff-130">그러나 식을 사용하여 파일 또는 폴더를 지정할 때 유효성 검사 오류가 발생하지 않도록 하려면 **파일 연결 관리자 편집기**에서 **파일/폴더**에 대해 파일 또는 폴더 경로를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-130">However, to avoid a validation error when you use an expression to specify the file or folder, in the **File Connection Manager Editor**, for **File/Folder**, add a file or folder path.</span></span>  
  
 <span data-ttu-id="cecff-131">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-131">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="cecff-132">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [파일 연결 관리자 편집기](../file-connection-manager-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cecff-132">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [File Connection Manager Editor](../file-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="cecff-133">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cecff-133">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
