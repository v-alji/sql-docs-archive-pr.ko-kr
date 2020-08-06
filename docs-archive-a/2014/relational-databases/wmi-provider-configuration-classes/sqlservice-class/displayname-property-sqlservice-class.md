---
title: DisplayName 속성 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- DisplayName Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- DisplayName property
ms.assetid: 49c408aa-6eb4-45cd-8d5c-60f065f24f5c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 147fc298d6d263caf1e4ad6852d4b02f86911572
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738110"
---
# <a name="displayname-property-sqlservice-class"></a><span data-ttu-id="beb4b-102">DisplayName 속성(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="beb4b-102">DisplayName Property (SqlService Class)</span></span>
  <span data-ttu-id="beb4b-103">서비스의 표시 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="beb4b-103">Gets the display name of the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beb4b-104">구문</span><span class="sxs-lookup"><span data-stu-id="beb4b-104">Syntax</span></span>  
  
```  
  
object  
.DisplayName [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="beb4b-105">부분</span><span class="sxs-lookup"><span data-stu-id="beb4b-105">Parts</span></span>  
 <span data-ttu-id="beb4b-106">*object*</span><span class="sxs-lookup"><span data-stu-id="beb4b-106">*object*</span></span>  
 <span data-ttu-id="beb4b-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4b-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="beb4b-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="beb4b-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="beb4b-109">서비스의 표시 이름을 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4b-109">A string value that specifies the display name of the service.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="beb4b-110">설명</span><span class="sxs-lookup"><span data-stu-id="beb4b-110">Remarks</span></span>  
 <span data-ttu-id="beb4b-111">이 문자열의 최대 길이는 256자입니다.</span><span class="sxs-lookup"><span data-stu-id="beb4b-111">This string has a maximum length of 256 characters.</span></span> <span data-ttu-id="beb4b-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 구성 관리자에서는 이름의 대/소문자가 유지되지만</span><span class="sxs-lookup"><span data-stu-id="beb4b-112">The name is case-preserved in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="beb4b-113">표시 이름을 비교할 때는 항상 대/소문자가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="beb4b-113">However, display name comparisons are always case-insensitive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="beb4b-114">예제</span><span class="sxs-lookup"><span data-stu-id="beb4b-114">Example</span></span>  
  
```  
mysqlservice.DisplayName = "Atdisk"  
```  
  
## <a name="see-also"></a><span data-ttu-id="beb4b-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="beb4b-115">See Also</span></span>  
 <span data-ttu-id="beb4b-116">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="beb4b-116">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
