---
title: 프로젝트를 배포한 후 매개 변수 값 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 39572594e429b61de0641c6e6929e84105138f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742392"
---
# <a name="set-parameter-values-after-the-project-is-deployed"></a><span data-ttu-id="0bab5-102">프로젝트를 배포한 후 매개 변수 값 설정</span><span class="sxs-lookup"><span data-stu-id="0bab5-102">Set Parameter Values After the Project Is Deployed</span></span>
  <span data-ttu-id="0bab5-103">카탈로그에 프로젝트를 배포할 때 배포 마법사를 사용하여 서버 기본 매개 변수 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bab5-103">The Deployment Wizard allows you to set server default parameter values when you deploy your project to the catalog.</span></span> <span data-ttu-id="0bab5-104">프로젝트가 카탈로그에 배포된 후 SSMS(SQL Server Management Studio) 개체 탐색기 또는 Transact-SQL을 사용하여 서버 기본값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bab5-104">After your project is in the catalog, you can use SQL Server Management Studio (SSMS) Object Explorer or Transact-SQL to set server default values.</span></span>  
  
### <a name="to-set-server-defaults-with-ssms-object-explorer"></a><span data-ttu-id="0bab5-105">SSMS 개체 탐색기를 사용하여 서버 기본값을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="0bab5-105">To set server defaults with SSMS Object Explorer:</span></span>  
  
1.  <span data-ttu-id="0bab5-106">**Integration Services** 노드 아래에서 프로젝트를 선택하고 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0bab5-106">Select and right-click the project under the **Integration Services** node.</span></span>  
  
2.  <span data-ttu-id="0bab5-107">**속성** 을 클릭하여 **프로젝트 속성** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0bab5-107">Click **Properties** to open the **Project Properties** dialog window.</span></span>  
  
3.  <span data-ttu-id="0bab5-108">**페이지 선택** 에서 **매개 변수**를 클릭하여 매개 변수 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0bab5-108">Open the parameters page by clicking **Parameters** under **Select a page**.</span></span>  
  
4.  <span data-ttu-id="0bab5-109">**매개 변수** 목록에서 원하는 매개 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0bab5-109">Select the desired parameter in the **Parameters** list.</span></span> <span data-ttu-id="0bab5-110">참고: **컨테이너** 열을 통해 패키지 매개 변수와 프로젝트 매개 변수를 구별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bab5-110">Note: The **Container** column helps distinguish project parameters from package parameters.</span></span>  
  
5.  <span data-ttu-id="0bab5-111">**값** 열에 원하는 서버 기본 매개 변수 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0bab5-111">In the **Value** column, specify the desired server default parameter value.</span></span>  
  
 <span data-ttu-id="0bab5-112">Transact-SQL로 서버 기본값을 설정하려면 [catalog.set_object_parameter_value&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database) 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0bab5-112">To set server defaults with Transact-SQL, use the [catalog.set_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database) stored procedure.</span></span> <span data-ttu-id="0bab5-113">현재 서버 기본값을 보려면 [catalog.object_parameters&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="0bab5-113">To view current server defaults, query the [catalog.object_parameters &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) view.</span></span> <span data-ttu-id="0bab5-114">서버 기본값을 지우려면 [catalog.clear_object_parameter_value&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database) 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0bab5-114">To clear a server default value, use the [catalog.clear_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database) stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bab5-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0bab5-115">See Also</span></span>  
 [<span data-ttu-id="0bab5-116">SSIS&#41; 매개 변수 &#40;Integration Services</span><span class="sxs-lookup"><span data-stu-id="0bab5-116">Integration Services &#40;SSIS&#41; Parameters</span></span>](integration-services-ssis-package-and-project-parameters.md)  
  
  
