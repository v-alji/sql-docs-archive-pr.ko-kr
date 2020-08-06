---
title: ResumeService 메서드 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ResumeService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ResumeService method
ms.assetid: 0b0a5f08-b95e-4626-bf81-309da7a0aacd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 53d07c8697c6303bc371f442745e2d1864682e40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649956"
---
# <a name="resumeservice-method-sqlservice-class"></a><span data-ttu-id="e0841-102">ResumeService 메서드(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="e0841-102">ResumeService Method (SqlService Class)</span></span>
  <span data-ttu-id="e0841-103">서비스를 재개된 상태로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0841-103">Attempts to place the service in the resumed state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0841-104">구문</span><span class="sxs-lookup"><span data-stu-id="e0841-104">Syntax</span></span>  
  
```  
  
object  
.ResumeService()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="e0841-105">부분</span><span class="sxs-lookup"><span data-stu-id="e0841-105">Parts</span></span>  
 <span data-ttu-id="e0841-106">*object*</span><span class="sxs-lookup"><span data-stu-id="e0841-106">*object*</span></span>  
 <span data-ttu-id="e0841-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e0841-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e0841-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="e0841-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="e0841-109">uint32 값으로, 0은 `ResumeService` 요청이 수락되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e0841-109">A uint32 value, which is 0 if the `ResumeService` request was accepted, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0841-110">설명</span><span class="sxs-lookup"><span data-stu-id="e0841-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0841-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0841-111">See Also</span></span>  
 <span data-ttu-id="e0841-112">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e0841-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
