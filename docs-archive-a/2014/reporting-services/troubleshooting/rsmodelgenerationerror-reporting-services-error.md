---
title: rsModelGenerationError - Reporting Services 오류 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 713de57f0f2957983966f8ef0345bb374c311781
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651454"
---
# <a name="rsmodelgenerationerror---reporting-services-error"></a><span data-ttu-id="c787d-102">rsModelGenerationError - Reporting Services 오류</span><span class="sxs-lookup"><span data-stu-id="c787d-102">rsModelGenerationError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="c787d-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="c787d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c787d-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="c787d-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="c787d-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="c787d-105">Event ID</span></span>|<span data-ttu-id="c787d-106">rsRenderingError</span><span class="sxs-lookup"><span data-stu-id="c787d-106">rsRenderingError</span></span>|  
|<span data-ttu-id="c787d-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="c787d-107">Event Source</span></span>|<span data-ttu-id="c787d-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="c787d-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="c787d-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="c787d-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="c787d-110">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="c787d-110">Message Text</span></span>|<span data-ttu-id="c787d-111">모델을 생성하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="c787d-111">An error occurred while generating model.</span></span> <span data-ttu-id="c787d-112">(rsModelGenerationError) (ReportingServicesLibrary) %1</span><span class="sxs-lookup"><span data-stu-id="c787d-112">(rsModelGenerationError) (ReportingServicesLibrary) %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c787d-113">설명</span><span class="sxs-lookup"><span data-stu-id="c787d-113">Explanation</span></span>  
 <span data-ttu-id="c787d-114">보고서 모델을 생성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c787d-114">The report model could not be generated.</span></span> <span data-ttu-id="c787d-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 SP1 및 이전 버전에서 이 오류는 예를 들어 두 개의 외래 키가 한 테이블 내에서 같은 열에 정의된 경우처럼 System.Data.DataSet 개체가 데이터베이스 스키마 내에서 테이블이나 관계를 처리할 수 없을 경우 주로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c787d-115">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 SP1 and earlier versions, this error is most likely displayed when the System.Data.DataSet object cannot handle a table or relationship within the database schema, such as when, for example, two foreign keys are defined on the same column within a table.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c787d-116">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="c787d-116">User Action</span></span>  
 <span data-ttu-id="c787d-117">이러한 메시지를 표시하는 특정 원인을 확인하려면 \Microsoft SQL Server\\<SQL Server Instance\>\Reporting Services\LogFiles에 있는 보고서 서버 로그 파일을 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="c787d-117">To determine the specific reason that caused this message to appear, review the report server log files, which are located at \Microsoft SQL Server\\<SQL Server Instance\>\Reporting Services\LogFiles.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="c787d-118">내부 전용</span><span class="sxs-lookup"><span data-stu-id="c787d-118">Internal-Only</span></span>  
  
