---
title: 테이블 형식 모델 데이터베이스에 대 한 메모리 내 또는 DirectQuery 액세스 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
author: minewiskan
ms.author: owend
ms.openlocfilehash: a607bc6c11f35736487932bdf10d239afc8b5355
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728840"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a><span data-ttu-id="08d27-102">테이블 형식 모델 데이터베이스에 대해 메모리 내 또는 DirectQuery 액세스 구성</span><span class="sxs-lookup"><span data-stu-id="08d27-102">Configure In-Memory or DirectQuery Access for a Tabular Model Database</span></span>
  <span data-ttu-id="08d27-103">이 항목에서는 직접 쿼리 모드에서 모델을 사용할 수 있도록 이미 배포된 테이블 형식 모델의 연결 속성을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="08d27-103">This topic describes how to change the connection properties of a tabular model that has already been deployed, to enable use of the model in Direct Query mode.</span></span>  
  
 <span data-ttu-id="08d27-104">이러한 속성에 대 한 자세한 내용과 가장 일반적인 시나리오에 대 한 구성 정보는 [DirectQuery 배포 시나리오 &#40;SSAS 테이블 형식&#41;](../directquery-deployment-scenarios-ssas-tabular.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="08d27-104">For more information about these properties, and configuration for the most common scenarios, see [DirectQuery Deployment Scenarios &#40;SSAS Tabular&#41;](../directquery-deployment-scenarios-ssas-tabular.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08d27-105">요구 사항</span><span class="sxs-lookup"><span data-stu-id="08d27-105">Requirements</span></span>  
 <span data-ttu-id="08d27-106">테이블 형식 모델에서 직접 쿼리 모드를 사용하도록 설정하는 작업은 다단계 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="08d27-106">Enabling the use of Direct Query mode on a tabular model is a multistep process.</span></span> <span data-ttu-id="08d27-107">다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="08d27-107">You must:</span></span>  
  
1.  <span data-ttu-id="08d27-108">모델에 직접 쿼리 모드에서 유효성 검사 오류를 일으킬 수 있는 기능이 없는지 확인</span><span class="sxs-lookup"><span data-stu-id="08d27-108">Ensure that the model does not have features which might cause validation errors in Direct Query mode.</span></span>  
  
2.  <span data-ttu-id="08d27-109">직접 쿼리를 지원하도록 모델의 스토리지 모드 변경</span><span class="sxs-lookup"><span data-stu-id="08d27-109">Change the storage mode on the model to support Direct Query.</span></span>  
  
3.  <span data-ttu-id="08d27-110">하이브리드 또는 순수 직접 쿼리 모드에서 쿼리를 지원하는 모드로 모델 배포</span><span class="sxs-lookup"><span data-stu-id="08d27-110">Deploy the model in a mode that supports queries in either a hybrid or pure Direct Query mode.</span></span>  
  
4.  <span data-ttu-id="08d27-111">직접 쿼리 모드를 지원하도록 배포된 데이터베이스의 연결 문자열 편집</span><span class="sxs-lookup"><span data-stu-id="08d27-111">Edit the connection string on the deployed database to support Direct Query mode.</span></span>  
  
 <span data-ttu-id="08d27-112">이 항목에서는 모델을 만들고 유효성을 검사했으며 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]와 같은 클라이언트에서 직접 쿼리 액세스를 사용하도록 설정하기만 하면 되는 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="08d27-112">This topic assumes that you have created and validated your model, and only need to enable Direct Query access from a client such as [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="08d27-113">절차</span><span class="sxs-lookup"><span data-stu-id="08d27-113">Procedure</span></span>  
  
#### <a name="change-the-connection-string-properties-of-the-model"></a><span data-ttu-id="08d27-114">모델의 연결 문자열 속성 변경</span><span class="sxs-lookup"><span data-stu-id="08d27-114">Change the Connection String Properties of the Model</span></span>  
  
1.  <span data-ttu-id="08d27-115">SQL Server Management Studio에서 모델을 배포한 인스턴스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="08d27-115">In SQL Server Management Studio, open the instance to which you deployed the model.</span></span>  
  
2.  <span data-ttu-id="08d27-116">개체 탐색기에서 모델 데이터베이스 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="08d27-116">In Object Explorer, right-click the name of the model database, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="08d27-117">**DirectQueryMode**속성을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="08d27-117">Locate the property, **DirectQueryMode**.</span></span> <span data-ttu-id="08d27-118">관계형 데이터 원본을 사용하려면 이 속성을 다음 값 중 하나로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08d27-118">To enable use of the relational data source, this property must be set to one of these values:</span></span>  
  
    -   <span data-ttu-id="08d27-119">**DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="08d27-119">**DirectQuery**</span></span>  
  
    -   <span data-ttu-id="08d27-120">**InMemoryWithDirectQuery**</span><span class="sxs-lookup"><span data-stu-id="08d27-120">**InMemoryWithDirectQuery**</span></span>  
  
    -   <span data-ttu-id="08d27-121">**DirectQueryWithInMemory**</span><span class="sxs-lookup"><span data-stu-id="08d27-121">**DirectQueryWithInMemory**</span></span>  
  
  
