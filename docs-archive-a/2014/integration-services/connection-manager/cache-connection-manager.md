---
title: 캐시 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Cache connection manager
ms.assetid: bdc92038-3720-4795-8a5c-79b963f2c952
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b8a7cc8bbe9e93c385fca6257e0be2e79bd3148a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651212"
---
# <a name="cache-connection-manager"></a><span data-ttu-id="c0415-102">캐시 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="c0415-102">Cache Connection Manager</span></span>
  <span data-ttu-id="c0415-103">캐시 연결 관리자는 캐시 변환이나 캐시 파일(.caw)에서 데이터를 읽고 이를 캐시 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-103">The Cache connection manager reads data from the Cache transform or from a cache file (.caw), and can save the data to a cache file.</span></span> <span data-ttu-id="c0415-104">캐시 연결 관리자가 캐시 파일을 사용하도록 구성했는지 여부에 관계없이 데이터는 항상 메모리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-104">Whether you configure the Cache connection manager to use a cache file, the data is always stored in memory.</span></span>  
  
 <span data-ttu-id="c0415-105">캐시 변환은 데이터 흐름에 있는 연결된 데이터 원본의 데이터를 캐시 연결 관리자에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-105">The Cache Transform transformation writes data from a connected data source in the data flow to a Cache connection manager.</span></span> <span data-ttu-id="c0415-106">패키지의 조회 변환은 데이터에 대해 조회를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-106">The Lookup transformation in a package performs lookups on the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0415-107">캐시 연결 관리자는 BLOB(Binary Large Object) 데이터 형식 DT_TEXT, DT_NTEXT 및 DT_IMAGE를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-107">The Cache connection manager does not support the Binary Large Object (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="c0415-108">참조 데이터 세트에 BLOB 데이터 형식이 있으면 패키지를 실행할 때 구성 요소가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-108">If the reference dataset contains a BLOB data type, the component will fail when you run the package.</span></span> <span data-ttu-id="c0415-109">**캐시 연결 관리자 편집기** 를 사용하여 열 데이터 형식을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-109">You can use the **Cache Connection Manager Editor** to modify column data types.</span></span> <span data-ttu-id="c0415-110">자세한 내용은 [Cache Connection Manager Editor](../cache-connection-manager-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0415-110">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0415-111">패키지의 보호 수준은 캐시 파일에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-111">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="c0415-112">캐시 파일에 중요한 정보가 들어 있는 경우 ACL(액세스 제어 목록)을 사용하여 파일 저장 위치 또는 폴더에 대한 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-112">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="c0415-113">특정 계정에 대해서만 액세스를 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-113">You should enable access only to certain accounts.</span></span> <span data-ttu-id="c0415-114">자세한 내용은 [패키지에서 사용되는 파일 액세스](../access-to-files-used-by-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0415-114">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
## <a name="configuration-of-the-cache-connection-manager"></a><span data-ttu-id="c0415-115">캐시 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="c0415-115">Configuration of the Cache Connection Manager</span></span>  
 <span data-ttu-id="c0415-116">다음과 같은 방법으로 캐시 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-116">You can configure the Cache connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="c0415-117">캐시 파일을 사용할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-117">Indicate whether to use a cache file.</span></span>  
  
     <span data-ttu-id="c0415-118">캐시 파일을 사용하도록 캐시 연결 관리자를 구성하면 연결 관리자는 다음 동작 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-118">If you configure the cache connection manager to use a cache file, the connection manager will do one of the following actions:</span></span>  
  
    -   <span data-ttu-id="c0415-119">캐시 변환이 데이터 흐름에 있는 데이터 원본의 데이터를 캐시 연결 관리자에 기록하도록 구성된 경우 데이터를 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-119">Save data to the file when a Cache Transform transformation is configured to write data from a data source in the data flow to the Cache connection manager.</span></span>  
  
    -   <span data-ttu-id="c0415-120">캐시 파일에서 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-120">Read data from the cache file.</span></span>  
  
     <span data-ttu-id="c0415-121">자세한 내용은 [Cache Transform](../data-flow/transformations/cache-transform.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0415-121">For more information, see [Cache Transform](../data-flow/transformations/cache-transform.md).</span></span>  
  
-   <span data-ttu-id="c0415-122">캐시에 저장된 열의 메타데이터를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-122">Change metadata for the columns stored in the cache.</span></span>  
  
-   <span data-ttu-id="c0415-123">런타임에 ConnectionString 속성을 설정하는 식을 사용하여 캐시 파일 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-123">Update the cache file name at runtime by using an expression to set the ConnectionString property.</span></span> <span data-ttu-id="c0415-124">자세한 내용은 [패키지에서 속성 식 사용](../expressions/use-property-expressions-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0415-124">For more information, see [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md).</span></span>  
  
 <span data-ttu-id="c0415-125">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0415-125">You can set properties through [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c0415-126">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [캐시 연결 관리자 편집기](../cache-connection-manager-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0415-126">For more information about the properties that you can set in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="c0415-127">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0415-127">For information about how to configure a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c0415-128">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c0415-128">Related Tasks</span></span>  
 [<span data-ttu-id="c0415-129">캐시 연결 관리자 변환을 사용하여 전체 캐시 모드에서 조회 변환 구현</span><span class="sxs-lookup"><span data-stu-id="c0415-129">Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager</span></span>](lookup-transformation-full-cache-mode-ole-db-connection-manager.md)  
  
  
