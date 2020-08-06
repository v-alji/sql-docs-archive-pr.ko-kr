---
title: StopService 메서드 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StopService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StopService method
ms.assetid: ef8e1856-4930-417a-8f52-be470fd3f15c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 534db69b9c5474638ef5e893847f7d6b9bbb645d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733708"
---
# <a name="stopservice-method-sqlservice-class"></a><span data-ttu-id="62214-102">StopService 메서드(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="62214-102">StopService Method (SqlService Class)</span></span>
  <span data-ttu-id="62214-103">서비스를 중지된 상태로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="62214-103">Attempts to place the service in the stopped state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62214-104">구문</span><span class="sxs-lookup"><span data-stu-id="62214-104">Syntax</span></span>  
  
```  
  
object  
.StopService()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="62214-105">부분</span><span class="sxs-lookup"><span data-stu-id="62214-105">Parts</span></span>  
 <span data-ttu-id="62214-106">*object*</span><span class="sxs-lookup"><span data-stu-id="62214-106">*object*</span></span>  
 <span data-ttu-id="62214-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="62214-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="62214-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="62214-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="62214-109">`uint32` 값으로, 0은 `ResumeService` 요청이 수락되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="62214-109">A `uint32` value, which is 0 if the `ResumeService` request was accepted, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62214-110">설명</span><span class="sxs-lookup"><span data-stu-id="62214-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62214-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62214-111">See Also</span></span>  
 <span data-ttu-id="62214-112">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="62214-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
