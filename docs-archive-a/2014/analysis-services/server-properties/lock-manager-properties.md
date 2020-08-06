---
title: 잠금 관리자 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- lock manager properties [Analysis Services]
- LockWaitGranularityMS property
- DefaultLockTimeoutMS property
- DeadlockDetectionGranularityMS property
ms.assetid: 15fe9ead-825b-4ac3-9191-7a07caa2861b
author: minewiskan
ms.author: owend
ms.openlocfilehash: d10927f1c549f00625b8affb801ec7b0831827c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743491"
---
# <a name="lock-manager-properties"></a><span data-ttu-id="e758e-102">잠금 관리자 속성</span><span class="sxs-lookup"><span data-stu-id="e758e-102">Lock Manager Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="e758e-103">에서는 다음 표에 나열된 잠금 관리자 서버 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e758e-103">supports the lock manager server properties listed in the following table.</span></span> <span data-ttu-id="e758e-104">추가 서버 속성 및 해당 속성 설정 방법은 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e758e-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="e758e-105">**적용 대상:** 다차원 및 테이블 형식 서버 모드</span><span class="sxs-lookup"><span data-stu-id="e758e-105">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e758e-106">속성</span><span class="sxs-lookup"><span data-stu-id="e758e-106">Properties</span></span>  
 `DefaultLockTimeoutMS`  
 <span data-ttu-id="e758e-107">내부 잠금 요청에 대한 기본 잠금 제한 시간(밀리초)을 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e758e-107">A signed 32-bit integer property that defines default lock timeout in milliseconds for internal lock requests.</span></span>  
  
 <span data-ttu-id="e758e-108">이 속성의 기본값은 -1로, 내부 잠금 요청에 대한 제한 시간이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e758e-108">The default value for this property is -1, which indicates there is no timeout for internal lock requests.</span></span>  
  
 `LockWaitGranularityMS`  
 <span data-ttu-id="e758e-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e758e-109">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DeadlockDetectionGranularityMS`  
 <span data-ttu-id="e758e-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e758e-110">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e758e-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e758e-111">See Also</span></span>  
 <span data-ttu-id="e758e-112">[Analysis Services에서 서버 속성 구성](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="e758e-112">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="e758e-113">Analysis Services 인스턴스의 서버 모드 확인</span><span class="sxs-lookup"><span data-stu-id="e758e-113">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
