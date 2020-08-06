---
title: ProcessId 클래스 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProcessId Class (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProcessId property
ms.assetid: 99b5a2e9-b44a-48a0-993e-04bd15c7fef4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7c4c40eea826b5009e52d26b1d930eaf5febbcdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650838"
---
# <a name="processid-class-sqlservice-class"></a><span data-ttu-id="bbd86-102">ProcessId 클래스(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="bbd86-102">ProcessId Class (SqlService Class)</span></span>
  <span data-ttu-id="bbd86-103">서비스를 고유하게 식별하는 시스템 프로세스 ID를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bbd86-103">Gets the system process ID that uniquely identifies a service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbd86-104">구문</span><span class="sxs-lookup"><span data-stu-id="bbd86-104">Syntax</span></span>  
  
```  
  
object  
.ProcessId [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="bbd86-105">부분</span><span class="sxs-lookup"><span data-stu-id="bbd86-105">Parts</span></span>  
 <span data-ttu-id="bbd86-106">*object*</span><span class="sxs-lookup"><span data-stu-id="bbd86-106">*object*</span></span>  
 <span data-ttu-id="bbd86-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="bbd86-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="bbd86-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="bbd86-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="bbd86-109">프로세스를 고유하게 식별하는 ID를 지정하는 `uint32` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="bbd86-109">A `uint32` value that specifies the ID that uniquely identifies the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbd86-110">설명</span><span class="sxs-lookup"><span data-stu-id="bbd86-110">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbd86-111">예제</span><span class="sxs-lookup"><span data-stu-id="bbd86-111">Example</span></span>  
  
```  
mysqlservice.ProcessId = 324  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbd86-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bbd86-112">See Also</span></span>  
 <span data-ttu-id="bbd86-113">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bbd86-113">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
