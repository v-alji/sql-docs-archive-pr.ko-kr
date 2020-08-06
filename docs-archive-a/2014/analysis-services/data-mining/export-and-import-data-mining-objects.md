---
title: 데이터 마이닝 개체 내보내기 및 가져오기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- exporting mining models
- exporting mining structures
- mining structures [Analysis Services], creating
- mining structures [DMX], exporting
- mining models [Analysis Services], migration
ms.assetid: 10a83b13-2640-4ff5-80c8-a35e1d692908
author: minewiskan
ms.author: owend
ms.openlocfilehash: 01e8651dd7e9d59012b0ba065bccb9ea62a1ee54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653051"
---
# <a name="export-and-import-data-mining-objects"></a><span data-ttu-id="8ab90-102">데이터 마이닝 개체 내보내기 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="8ab90-102">Export and Import Data Mining Objects</span></span>
  <span data-ttu-id="8ab90-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 제공하는 솔루션 백업, 복원 및 마이그레이션 기능 이외에도 SQL Server 데이터 마이닝을 통해 DMX(Data Mining Extensions)를 사용하여 서로 다른 서버 간에 데이터 마이닝 구조 및 모델을 빠르게 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-103">In addition to the functionality provided in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for backing up, restoring, and migrating solutions, SQL Server Data Mining provides the ability to quickly transfer data mining structures and models between different servers by using Data Mining Extensions (DMX).</span></span>  
  
 <span data-ttu-id="8ab90-104">데이터 마이닝 솔루션에 다차원 데이터베이스 대신 관계형 데이터가 사용된 경우, 데이터베이스 복원을 사용하거나 전체 솔루션을 배포하는 방법보다 `EXPORT` 및 `IMPORT`를 사용하여 모델을 전송하는 방법이 훨씬 손쉽고 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-104">If your data mining solution uses relational data instead of a multidimensional database, transferring models by using `EXPORT` and `IMPORT` is much faster and easier than either using database restore or deploying an entire solution.</span></span>  
  
 <span data-ttu-id="8ab90-105">이 섹션에서는 DMX 문을 사용하여 데이터 마이닝 구조 및 모델을 전송하는 방법을 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-105">This section provides an overview of how to transfer data mining structures and models by using DMX statements.</span></span> <span data-ttu-id="8ab90-106">자세한 구문 및 예제는 [EXPORT&#40;DMX&#41;](/sql/dmx/export-dmx) 및 [IMPORT&#40;DMX&#41;](/sql/dmx/import-dmx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ab90-106">For details of the syntax, together with examples, see [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx) and [IMPORT &#40;DMX&#41;](/sql/dmx/import-dmx).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ab90-107">Microsoft SQL Server Analysis Services 데이터베이스에서 개체를 내보내거나 가져오려면 데이터베이스 관리자 또는 서버 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-107">You must be a database or server administrator to export or import objects from a Microsoft SQL Server Analysis Services database.</span></span>  
  
## <a name="exporting-data-mining-structures"></a><span data-ttu-id="8ab90-108">데이터 마이닝 구조 내보내기</span><span class="sxs-lookup"><span data-stu-id="8ab90-108">Exporting Data Mining Structures</span></span>  
 <span data-ttu-id="8ab90-109">EXPORT 문을 사용하여 마이닝 구조를 내보내면 모든 관련 모델이 자동으로 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-109">When you export a mining structure, the EXPORT statement automatically exports all associated models.</span></span> <span data-ttu-id="8ab90-110">내보낼 개체를 제어하려면 각 개체의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-110">If you want to control the objects that are exported, you must specify each object by name.</span></span>  
  
 <span data-ttu-id="8ab90-111">마이닝 구조를 내보낼 때 기본 동작에 따라 마이닝 구조가 처리되어 결과가 캐시된 경우, 구조의 기반이 되는 데이터에 대한 요약이 정의에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-111">If the mining structure has been processed and the results have been cached, which is the default behavior, when you export the mining structure, the definition contains a summary of the data on which the structure is based.</span></span> <span data-ttu-id="8ab90-112">이러한 요약을 제거하려면 `Process Clear Structure` 작업을 수행하여 마이닝 구조에 연결된 캐시를 지워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-112">To remove this summary, you must clear the cache associated with the mining structure by performing a `Process Clear Structure` operation.</span></span> <span data-ttu-id="8ab90-113">자세한 내용은 [Process a Mining Structure](process-a-mining-structure.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ab90-113">For more information, see [Process a Mining Structure](process-a-mining-structure.md).</span></span>  
  
### <a name="exporting-data-mining-models"></a><span data-ttu-id="8ab90-114">데이터 마이닝 모델 내보내기</span><span class="sxs-lookup"><span data-stu-id="8ab90-114">Exporting Data Mining Models</span></span>  
 <span data-ttu-id="8ab90-115">`WITH DEPENDENCIES` 키워드를 사용하면 마이닝 모델 및 해당 구조와 함께 데이터 원본 및 데이터 원본 뷰 정의를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-115">You can use the `WITH DEPENDENCIES` keyword to export the data source and data source view definition together with the mining model and its structure.</span></span>  
  
 <span data-ttu-id="8ab90-116">해당 종속성을 내보내지 않고 마이닝 모델을 내보내면 EXPORT 문에서 마이닝 모델의 정의 및 해당 마이닝 구조를 내보내지만 데이터 원본의 정의는 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-116">When you export a mining model without exporting its dependencies, the EXPORT statement will export the definition of the mining model and its mining structure, but does not export the definition of the data sources.</span></span> <span data-ttu-id="8ab90-117">따라서 모델을 가져온 후 모델을 즉시 찾아볼 수 있지만 대상 서버에서 마이닝 모델을 다시 처리하거나 기본 데이터에 대해 쿼리를 실행하려면 대상 서버에 해당 데이터 원본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-117">As a consequence, after you import the model you will be able to browse the model immediately, but if you want to reprocess the mining model on the target server, or run queries against the underlying data, you must create a corresponding data source on the destination server.</span></span>  
  
## <a name="importing-data-mining-structures-and-models"></a><span data-ttu-id="8ab90-118">데이터 마이닝 구조 및 모델 가져오기</span><span class="sxs-lookup"><span data-stu-id="8ab90-118">Importing Data Mining Structures and Models</span></span>  
 <span data-ttu-id="8ab90-119">데이터 마이닝 개체를 가져오면 IMPORT 문을 실행할 때 연결되어 있는 서버 및 데이터베이스로 개체를 가져오게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-119">When you import a data mining object, the object is imported to the server and database to which you are connected when you execute the IMPORT statement.</span></span> <span data-ttu-id="8ab90-120">서버에 없는 데이터베이스가 가져오기 파일에 포함된 경우 해당 데이터베이스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-120">If the import file includes a database that does not exist on the server, the database will be created.</span></span>  
  
 <span data-ttu-id="8ab90-121">`Restore` 명령을 사용하여 마이닝 구조 또는 마이닝 모델을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-121">You can also import a mining structure or mining model by using the `Restore` command.</span></span> <span data-ttu-id="8ab90-122">이러한 모델이나 구조를 내보낸 데이터베이스와 같은 이름의 데이터베이스에 해당 모델이나 구조가 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-122">Your models or structures will be restored into the database that has the same name as the database from which they were exported.</span></span> <span data-ttu-id="8ab90-123">자세한 내용은 [Restore Options](../multidimensional-models/restore-options.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ab90-123">For more information, see [Restore Options](../multidimensional-models/restore-options.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ab90-124">설명</span><span class="sxs-lookup"><span data-stu-id="8ab90-124">Remarks</span></span>  
 <span data-ttu-id="8ab90-125">서버에 이름이 같은 모델이나 구조가 이미 있으면 해당 서버로 모델이나 구조를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-125">You cannot import a model or structure to a server if a model or structure of the same name already exists on that server.</span></span> <span data-ttu-id="8ab90-126">또한 데이터 마이닝 개체를 내보낸 다음 내보내기 파일에서 해당 개체의 이름을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-126">Also, you cannot export a data mining object and then modify the name of that object in the export file.</span></span> <span data-ttu-id="8ab90-127">따라서 이름이 충돌할 것으로 예상되는 경우 대상 서버에서 데이터 마이닝 개체를 삭제하거나 정의를 내보내기 전에 데이터 마이닝 개체의 이름을 바꿔야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab90-127">Therefore, if you anticipate naming conflicts, you should either delete the data mining object on the target server, or rename the data mining object before you export the definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab90-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ab90-128">See Also</span></span>  
 [<span data-ttu-id="8ab90-129">데이터 마이닝 솔루션 및 개체 관리</span><span class="sxs-lookup"><span data-stu-id="8ab90-129">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
  
