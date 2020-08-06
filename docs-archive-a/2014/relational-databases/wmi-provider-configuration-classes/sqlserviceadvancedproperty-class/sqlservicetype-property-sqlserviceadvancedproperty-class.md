---
title: SqlServiceType 속성 (SqlServiceAdvancedProperty 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SqlServiceType Property (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServiceType property
ms.assetid: 20f1663a-9a14-4f14-8c1b-8aa133e272c3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 774c8599fd21e330fa3228336ab1ed3c73d65c85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660928"
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a><span data-ttu-id="75efb-102">SqlServiceType 속성(SqlServiceAdvancedProperty 클래스)</span><span class="sxs-lookup"><span data-stu-id="75efb-102">SqlServiceType Property (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="75efb-103">고급 속성과 연결된 관리되는 서비스의 유형을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="75efb-103">Gets the type of the managed service associated with the advanced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75efb-104">구문</span><span class="sxs-lookup"><span data-stu-id="75efb-104">Syntax</span></span>  
  
```  
  
object  
.SetBoolValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="75efb-105">부분</span><span class="sxs-lookup"><span data-stu-id="75efb-105">Parts</span></span>  
 <span data-ttu-id="75efb-106">*object*</span><span class="sxs-lookup"><span data-stu-id="75efb-106">*object*</span></span>  
 <span data-ttu-id="75efb-107">고급 속성을 나타내는 [SqlServiceAdvancedProperty 클래스](sqlserviceadvancedproperty-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="75efb-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="75efb-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="75efb-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="75efb-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스 유형을 지정하는 uint32 값입니다.</span><span class="sxs-lookup"><span data-stu-id="75efb-109">A uint32 value that specifies the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75efb-110">설명</span><span class="sxs-lookup"><span data-stu-id="75efb-110">Remarks</span></span>  
 <span data-ttu-id="75efb-111">반환 값은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75efb-111">Return values can be one of the following:</span></span>  
  
|<span data-ttu-id="75efb-112">Type</span><span class="sxs-lookup"><span data-stu-id="75efb-112">Type</span></span>|<span data-ttu-id="75efb-113">정의</span><span class="sxs-lookup"><span data-stu-id="75efb-113">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="75efb-114">*1*</span><span class="sxs-lookup"><span data-stu-id="75efb-114">*1*</span></span>|<span data-ttu-id="75efb-115">MSSQLSERVER는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="75efb-115">MSSQLSERVER is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="75efb-116">*2*</span><span class="sxs-lookup"><span data-stu-id="75efb-116">*2*</span></span>|<span data-ttu-id="75efb-117">SQLSERVERAGENT는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에이전트 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="75efb-117">SQLSERVERAGENT is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service.</span></span>|  
|<span data-ttu-id="75efb-118">*3*</span><span class="sxs-lookup"><span data-stu-id="75efb-118">*3*</span></span>|<span data-ttu-id="75efb-119">MSFTESQL은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 전체 텍스트 검색 엔진 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="75efb-119">MSFTESQL is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Full-text Search Engine service.</span></span>|  
|<span data-ttu-id="75efb-120">*4*</span><span class="sxs-lookup"><span data-stu-id="75efb-120">*4*</span></span>|<span data-ttu-id="75efb-121">MsDtsServer는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="75efb-121">MsDtsServer is the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="75efb-122">*5*</span><span class="sxs-lookup"><span data-stu-id="75efb-122">*5*</span></span>|<span data-ttu-id="75efb-123">MSSQLServerOLAPService는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="75efb-123">MSSQLServerOLAPService is the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="75efb-124">*6*</span><span class="sxs-lookup"><span data-stu-id="75efb-124">*6*</span></span>|<span data-ttu-id="75efb-125">ReportServer는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="75efb-125">ReportServer is the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="75efb-126">*7*</span><span class="sxs-lookup"><span data-stu-id="75efb-126">*7*</span></span>|<span data-ttu-id="75efb-127">SQLBrowser는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="75efb-127">SQLBrowser is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75efb-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75efb-128">See Also</span></span>  
 <span data-ttu-id="75efb-129">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="75efb-129">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
