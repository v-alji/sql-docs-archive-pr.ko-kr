---
title: 예약 된 ORDPATH 데이터 형식 다음에 명명 된 UDT&#39;제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 474e910a-6abb-4e28-acc2-055338c011d4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0528d19de17781d863e3a42fdef7db558fe5d190
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742803"
---
# <a name="remove-udt39s-named-after-the-reserved-ordpath-data-type"></a>예약 된 ORDPATH 데이터 형식 다음에 명명 된 UDT&#39;제거
  업그레이드 관리자가 `ORDPATH` 데이터 형식용으로 예약된 용어를 따서 명명된 UDT(사용자 정의 형식)를 발견했습니다.  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>설명  
 기본 제공 데이터 형식에 사용되는 용어는 CLR(공용 언어 런타임) 또는 별칭 UDT의 이름으로 사용할 수 없습니다.  
  
## <a name="corrective-action"></a>수정 동작  
 데이터 형식의 이름을 따서 명명된 UDT를 제거하고 예약되지 않은 이름을 사용하여 UDT를 다시 만듭니다.  
  
## <a name="external-resources"></a>외부 리소스  
 [사용자 정의 형식 만들기](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
